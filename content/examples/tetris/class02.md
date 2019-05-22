---
title: "Draw squares"
date: 2019-05-21T17:36:23+08:00
weight: 2
pre: "<b>2. </b>"
chapter: false
---

### Before today's class

|<center>Task</center> 	   |         <center>Time</center>                   |
---------- | -------------------------------- |
| <center>Quickly go through the [**previous class**](/examples/tetris/class01)</center>  | <center>10 mins</center>  |

In the previous class, we've set up the basic structure of the tetris game. In this class, we're going to customize the game screen and add squares.

### The customize version of the code

    import sys, random
    from PyQt5.QtWidgets import QMainWindow, QFrame, QDesktopWidget, QApplication, QHBoxLayout, QLabel
    from PyQt5.QtCore import Qt, QBasicTimer, pyqtSignal
    from PyQt5.QtGui import QPainter, QColor

    from tetris_model import BOARD_DATA, Shape
    from tetris_ai import TETRIS_AI

    # TETRIS_AI = None

    class Tetris(QMainWindow):
        def __init__(self):
            super().__init__()
            self.isStarted = False
            self.isPaused = False
            self.nextMove = None
            self.lastShape = Shape.shapeNone

            self.initUI()

        def initUI(self):
            self.gridSize = 22
            self.speed = 10

            self.timer = QBasicTimer()
            self.setFocusPolicy(Qt.StrongFocus)

            hLayout = QHBoxLayout()
            self.tboard = Board(self, self.gridSize)
            hLayout.addWidget(self.tboard)

            self.sidePanel = SidePanel(self, self.gridSize)
            hLayout.addWidget(self.sidePanel)

            self.statusbar = self.statusBar()
            self.tboard.msg2Statusbar[str].connect(self.statusbar.showMessage)
            
            self.setWindowTitle('Tetris')
            self.show()

            self.setFixedSize(self.tboard.width() + self.sidePanel.width(),
                              self.sidePanel.height() + self.statusbar.height())

    class SidePanel(QFrame):
        def __init__(self, parent, gridSize):
            super().__init__(parent)
            self.setFixedSize(gridSize * 5, gridSize * BOARD_DATA.height)
            self.move(gridSize * BOARD_DATA.width, 0)
            self.gridSize = gridSize

        def updateData(self):
            self.update()

        def paintEvent(self, event):
            painter = QPainter(self)
            minX, maxX, minY, maxY = BOARD_DATA.nextShape.getBoundingOffsets(0)

            dy = 3 * self.gridSize
            dx = (self.width() - (maxX - minX) * self.gridSize) / 2

            val = BOARD_DATA.nextShape.shape
            for x, y in BOARD_DATA.nextShape.getCoords(0, 0, -minY):
                drawSquare(painter, x * self.gridSize + dx, y * self.gridSize + dy, val, self.gridSize)

    class Board(QFrame):
        msg2Statusbar = pyqtSignal(str)
        speed = 10

        def __init__(self, parent, gridSize):
            super().__init__(parent)
            self.setFixedSize(gridSize * BOARD_DATA.width, gridSize * BOARD_DATA.height)
            self.gridSize = gridSize
            self.initBoard()

        def initBoard(self):
            self.score = 0
            BOARD_DATA.clear()

        def paintEvent(self, event):
            painter = QPainter(self)

            # Draw backboard
            for x in range(BOARD_DATA.width):
                for y in range(BOARD_DATA.height):
                    val = BOARD_DATA.getValue(x, y)
                    drawSquare(painter, x * self.gridSize, y * self.gridSize, val, self.gridSize)

            # Draw current shape
            for x, y in BOARD_DATA.getCurrentShapeCoord():
                val = BOARD_DATA.currentShape.shape
                drawSquare(painter, x * self.gridSize, y * self.gridSize, val, self.gridSize)

            # Draw a border
            painter.setPen(QColor(0x777777))
            painter.drawLine(self.width()-1, 0, self.width()-1, self.height())
            painter.setPen(QColor(0xCCCCCC))
            painter.drawLine(self.width(), 0, self.width(), self.height())

        def updateData(self):
            self.msg2Statusbar.emit(str(self.score))
            self.update()


    if __name__ == '__main__':
        # random.seed(32)
        app = QApplication([])
        tetris = Tetris()
        sys.exit(app.exec_())

### Step 1: Set the squares to the center of the screen

	    def center(self):
            screen = QDesktopWidget().screenGeometry()
            size = self.geometry()
            self.move((screen.width() - size.width()) // 2, (screen.height() - size.height()) // 2)

Set the game window to the center.

### Step 2: Update the window

	def updateWindow(self):
        self.tboard.updateData()
        self.sidePanel.updateData()
        self.update() 

Update the window by calling this function whenever it's necessary.

### Step 3: Start the game

	def start(self):
        if self.isPaused:
            return

        self.isStarted = True
        self.tboard.score = 0
        BOARD_DATA.clear()

        self.tboard.msg2Statusbar.emit(str(self.tboard.score))

        BOARD_DATA.createNewPiece()
        self.timer.start(self.speed, self)

Call this start function in the tetris class instantiation to start the game.

### Step 4: Pause the game

	    def pause(self):
	        if not self.isStarted:
	            return

	        self.isPaused = not self.isPaused

	        if self.isPaused:
	            self.timer.stop()
	            self.tboard.msg2Statusbar.emit("paused")
	        else:
	            self.timer.start(self.speed, self)

	        self.updateWindow()

Whenever the game state is paused, timer and board state will also be paused.

### Step 5: Key press event

An event is an entity which encapsulates the action and the contextual variables triggering the action.Events can be generated or triggered by the system, by the user or in other ways.

For Example:

- Keystrokes on the keyboard
- Hardware device like a timer
- Mouse click
- Sensors
- Messages from other application

	    def keyPressEvent(self, event):
	        if not self.isStarted or BOARD_DATA.currentShape == Shape.shapeNone:
	            super(Tetris, self).keyPressEvent(event)
	            return

	        key = event.key()
	        
	        if key == Qt.Key_P:
	            self.pause()
	            return
	            
	        if self.isPaused:
	            return
	        elif key == Qt.Key_Left:
	            BOARD_DATA.moveLeft()
	        elif key == Qt.Key_Right:
	            BOARD_DATA.moveRight()
	        elif key == Qt.Key_Up:
	            BOARD_DATA.rotateLeft()
	        elif key == Qt.Key_Space:
	            self.tboard.score += BOARD_DATA.dropDown()
	        else:
	            super(Tetris, self).keyPressEvent(event)

	        self.updateWindow()

Press event listens to each key press of changing the square state such as shape, direction,etc.

### Step 6: Draw the squares

	def drawSquare(painter, x, y, val, s):
	    colorTable = [0x000000, 0xCC6666, 0x66CC66, 0x6666CC,
	                  0xCCCC66, 0xCC66CC, 0x66CCCC, 0xDAAA00]

	    if val == 0:
	        return

	    color = QColor(colorTable[val])
	    painter.fillRect(x + 1, y + 1, s - 2, s - 2, color)

	    painter.setPen(color.lighter())
	    painter.drawLine(x, y + s - 1, x, y)
	    painter.drawLine(x, y, x + s - 1, y)

	    painter.setPen(color.darker())
	    painter.drawLine(x + 1, y + s - 1, x + s - 1, y + s - 1)
	    painter.drawLine(x + s - 1, y + s - 1, x + s - 1, y + 1)

Draw the squares to present on the game screen. In this function, we have [**List**](/basics/list) to store different colors.

### Step 7: Put them all together in to the workflow

    import sys, random
    from PyQt5.QtWidgets import QMainWindow, QFrame, QDesktopWidget, QApplication, QHBoxLayout, QLabel
    from PyQt5.QtCore import Qt, QBasicTimer, pyqtSignal
    from PyQt5.QtGui import QPainter, QColor

    from tetris_model import BOARD_DATA, Shape
    from tetris_ai import TETRIS_AI

    # TETRIS_AI = None

    class Tetris(QMainWindow):
        def __init__(self):
            super().__init__()
            self.isStarted = False
            self.isPaused = False
            self.nextMove = None
            self.lastShape = Shape.shapeNone

            self.initUI()

        def initUI(self):
            self.gridSize = 22
            self.speed = 10

            self.timer = QBasicTimer()
            self.setFocusPolicy(Qt.StrongFocus)

            hLayout = QHBoxLayout()
            self.tboard = Board(self, self.gridSize)
            hLayout.addWidget(self.tboard)

            self.sidePanel = SidePanel(self, self.gridSize)
            hLayout.addWidget(self.sidePanel)

            self.statusbar = self.statusBar()
            self.tboard.msg2Statusbar[str].connect(self.statusbar.showMessage)

            self.start()

            self.center()
            self.setWindowTitle('Tetris')
            self.show()

            self.setFixedSize(self.tboard.width() + self.sidePanel.width(),
                              self.sidePanel.height() + self.statusbar.height())
        def center(self):
            screen = QDesktopWidget().screenGeometry()
            size = self.geometry()
            self.move((screen.width() - size.width()) // 2, (screen.height() - size.height()) // 2)

        def start(self):
            if self.isPaused:
                return

            self.isStarted = True
            self.tboard.score = 0
            BOARD_DATA.clear()

            self.tboard.msg2Statusbar.emit(str(self.tboard.score))

            BOARD_DATA.createNewPiece()
            self.timer.start(self.speed, self)

        def pause(self):
            if not self.isStarted:
                return

            self.isPaused = not self.isPaused

            if self.isPaused:
                self.timer.stop()
                self.tboard.msg2Statusbar.emit("paused")
            else:
                self.timer.start(self.speed, self)

            self.updateWindow()

        def updateWindow(self):
            self.tboard.updateData()
            self.sidePanel.updateData()
            self.update()

        def keyPressEvent(self, event):
            if not self.isStarted or BOARD_DATA.currentShape == Shape.shapeNone:
                super(Tetris, self).keyPressEvent(event)
                return

            key = event.key()
            
            if key == Qt.Key_P:
                self.pause()
                return
                
            if self.isPaused:
                return
            elif key == Qt.Key_Left:
                BOARD_DATA.moveLeft()
            elif key == Qt.Key_Right:
                BOARD_DATA.moveRight()
            elif key == Qt.Key_Up:
                BOARD_DATA.rotateLeft()
            elif key == Qt.Key_Space:
                self.tboard.score += BOARD_DATA.dropDown()
            else:
                super(Tetris, self).keyPressEvent(event)

            self.updateWindow()

    def drawSquare(painter, x, y, val, s):
        colorTable = [0x000000, 0xCC6666, 0x66CC66, 0x6666CC,
                      0xCCCC66, 0xCC66CC, 0x66CCCC, 0xDAAA00]

        if val == 0:
            return

        color = QColor(colorTable[val])
        painter.fillRect(x + 1, y + 1, s - 2, s - 2, color)

        painter.setPen(color.lighter())
        painter.drawLine(x, y + s - 1, x, y)
        painter.drawLine(x, y, x + s - 1, y)

        painter.setPen(color.darker())
        painter.drawLine(x + 1, y + s - 1, x + s - 1, y + s - 1)
        painter.drawLine(x + s - 1, y + s - 1, x + s - 1, y + 1)

    class SidePanel(QFrame):
        def __init__(self, parent, gridSize):
            super().__init__(parent)
            self.setFixedSize(gridSize * 5, gridSize * BOARD_DATA.height)
            self.move(gridSize * BOARD_DATA.width, 0)
            self.gridSize = gridSize

        def updateData(self):
            self.update()

        def paintEvent(self, event):
            painter = QPainter(self)
            minX, maxX, minY, maxY = BOARD_DATA.nextShape.getBoundingOffsets(0)

            dy = 3 * self.gridSize
            dx = (self.width() - (maxX - minX) * self.gridSize) / 2

            val = BOARD_DATA.nextShape.shape
            for x, y in BOARD_DATA.nextShape.getCoords(0, 0, -minY):
                drawSquare(painter, x * self.gridSize + dx, y * self.gridSize + dy, val, self.gridSize)

    class Board(QFrame):
        msg2Statusbar = pyqtSignal(str)
        speed = 10

        def __init__(self, parent, gridSize):
            super().__init__(parent)
            self.setFixedSize(gridSize * BOARD_DATA.width, gridSize * BOARD_DATA.height)
            self.gridSize = gridSize
            self.initBoard()

        def initBoard(self):
            self.score = 0
            BOARD_DATA.clear()

        def paintEvent(self, event):
            painter = QPainter(self)

            # Draw backboard
            for x in range(BOARD_DATA.width):
                for y in range(BOARD_DATA.height):
                    val = BOARD_DATA.getValue(x, y)
                    drawSquare(painter, x * self.gridSize, y * self.gridSize, val, self.gridSize)

            # Draw current shape
            for x, y in BOARD_DATA.getCurrentShapeCoord():
                val = BOARD_DATA.currentShape.shape
                drawSquare(painter, x * self.gridSize, y * self.gridSize, val, self.gridSize)

            # Draw a border
            painter.setPen(QColor(0x777777))
            painter.drawLine(self.width()-1, 0, self.width()-1, self.height())
            painter.setPen(QColor(0xCCCCCC))
            painter.drawLine(self.width(), 0, self.width(), self.height())

        def updateData(self):
            self.msg2Statusbar.emit(str(self.score))
            self.update()


    if __name__ == '__main__':
        # random.seed(32)
        app = QApplication([])
        tetris = Tetris()
        sys.exit(app.exec_())

