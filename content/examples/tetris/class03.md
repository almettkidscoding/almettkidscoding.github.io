---
title: "AI model integration"
date: 2019-06-18T18:36:19+08:00
weight: 3
pre: "<b>3. </b>"
chapter: false
---

### Before today's class

|<center>Task</center> 	   |         <center>Time</center>                   |
---------- | -------------------------------- |
| <center>Quickly go through the [**Previous class**](/examples/tetris/class02)</center>  | <center>10 mins</center>  |

In the previous class, we’ve set up the basic structure of the tetris game. In this class, we’re going to customize the game screen and add squares.

### Tetris game architecture

Following is the basic architecture of the tetris game. The game hierarchy is seperated to three layers:

- AI layer
- Basics layer
- Infrastructure layer

![](/images/tetris_game_workflow.jpg)

In this class, we will integrate our Tetris game with AI model.

### Step 1: Create AI workflow

1. Under the same directory of `tetris_game.py` file create `tetris_ai.py` and copy/paste following code.

2. This module leverages data and algorithms from the `etris_model.py` file, helps us integrate the AI model with our general tetris game and make it smarter. We call this process workflow.

from tetris_model import BOARD_DATA, Shape import math from datetime import datetime import numpy as np

	class TetrisAI(object):

    def nextMove(self):
        t1 = datetime.now()
        if BOARD_DATA.currentShape == Shape.shapeNone:
            return None

        currentDirection = BOARD_DATA.currentDirection
        currentY = BOARD_DATA.currentY
        _, _, minY, _ = BOARD_DATA.nextShape.getBoundingOffsets(0)
        nextY = -minY

        # print("=======")
        strategy = None
        if BOARD_DATA.currentShape.shape in (Shape.shapeI, Shape.shapeZ, Shape.shapeS):
            d0Range = (0, 1)
        elif BOARD_DATA.currentShape.shape == Shape.shapeO:
            d0Range = (0,)
        else:
            d0Range = (0, 1, 2, 3)

        if BOARD_DATA.nextShape.shape in (Shape.shapeI, Shape.shapeZ, Shape.shapeS):
            d1Range = (0, 1)
        elif BOARD_DATA.nextShape.shape == Shape.shapeO:
            d1Range = (0,)
        else:
            d1Range = (0, 1, 2, 3)

        for d0 in d0Range:
            minX, maxX, _, _ = BOARD_DATA.currentShape.getBoundingOffsets(d0)
            for x0 in range(-minX, BOARD_DATA.width - maxX):
                board = self.calcStep1Board(d0, x0)
                for d1 in d1Range:
                    minX, maxX, _, _ = BOARD_DATA.nextShape.getBoundingOffsets(d1)
                    dropDist = self.calcNextDropDist(board, d1, range(-minX, BOARD_DATA.width - maxX))
                    for x1 in range(-minX, BOARD_DATA.width - maxX):
                        score = self.calculateScore(np.copy(board), d1, x1, dropDist)
                        if not strategy or strategy[2] < score:
                            strategy = (d0, x0, score)
        print("===", datetime.now() - t1)
        return strategy

    def calcNextDropDist(self, data, d0, xRange):
        res = {}
        for x0 in xRange:
            if x0 not in res:
                res[x0] = BOARD_DATA.height - 1
            for x, y in BOARD_DATA.nextShape.getCoords(d0, x0, 0):
                yy = 0
                while yy + y < BOARD_DATA.height and (yy + y < 0 or data[(y + yy), x] == Shape.shapeNone):
                    yy += 1
                yy -= 1
                if yy < res[x0]:
                    res[x0] = yy
        return res

    def calcStep1Board(self, d0, x0):
        board = np.array(BOARD_DATA.getData()).reshape((BOARD_DATA.height, BOARD_DATA.width))
        self.dropDown(board, BOARD_DATA.currentShape, d0, x0)
        return board

    def dropDown(self, data, shape, direction, x0):
        dy = BOARD_DATA.height - 1
        for x, y in shape.getCoords(direction, x0, 0):
            yy = 0
            while yy + y < BOARD_DATA.height and (yy + y < 0 or data[(y + yy), x] == Shape.shapeNone):
                yy += 1
            yy -= 1
            if yy < dy:
                dy = yy
        # print("dropDown: shape {0}, direction {1}, x0 {2}, dy {3}".format(shape.shape, direction, x0, dy))
        self.dropDownByDist(data, shape, direction, x0, dy)

    def dropDownByDist(self, data, shape, direction, x0, dist):
        for x, y in shape.getCoords(direction, x0, 0):
            data[y + dist, x] = shape.shape

    def calculateScore(self, step1Board, d1, x1, dropDist):
        # print("calculateScore")
        t1 = datetime.now()
        width = BOARD_DATA.width
        height = BOARD_DATA.height

        self.dropDownByDist(step1Board, BOARD_DATA.nextShape, d1, x1, dropDist[x1])
        # print(datetime.now() - t1)

        # Term 1: lines to be removed
        fullLines, nearFullLines = 0, 0
        roofY = [0] * width
        holeCandidates = [0] * width
        holeConfirm = [0] * width
        vHoles, vBlocks = 0, 0
        for y in range(height - 1, -1, -1):
            hasHole = False
            hasBlock = False
            for x in range(width):
                if step1Board[y, x] == Shape.shapeNone:
                    hasHole = True
                    holeCandidates[x] += 1
                else:
                    hasBlock = True
                    roofY[x] = height - y
                    if holeCandidates[x] > 0:
                        holeConfirm[x] += holeCandidates[x]
                        holeCandidates[x] = 0
                    if holeConfirm[x] > 0:
                        vBlocks += 1
            if not hasBlock:
                break
            if not hasHole and hasBlock:
                fullLines += 1
        vHoles = sum([x ** .7 for x in holeConfirm])
        maxHeight = max(roofY) - fullLines
        # print(datetime.now() - t1)

        roofDy = [roofY[i] - roofY[i+1] for i in range(len(roofY) - 1)]

        if len(roofY) <= 0:
            stdY = 0
        else:
            stdY = math.sqrt(sum([y ** 2 for y in roofY]) / len(roofY) - (sum(roofY) / len(roofY)) ** 2)
        if len(roofDy) <= 0:
            stdDY = 0
        else:
            stdDY = math.sqrt(sum([y ** 2 for y in roofDy]) / len(roofDy) - (sum(roofDy) / len(roofDy)) ** 2)

        absDy = sum([abs(x) for x in roofDy])
        maxDy = max(roofY) - min(roofY)
        # print(datetime.now() - t1)

        score = fullLines * 1.8 - vHoles * 1.0 - vBlocks * 0.5 - maxHeight ** 1.5 * 0.02 \
            - stdY * 0.0 - stdDY * 0.01 - absDy * 0.2 - maxDy * 0.3
        # print(score, fullLines, vHoles, vBlocks, maxHeight, stdY, stdDY, absDy, roofY, d0, x0, d1, x1)
        return score

TETRIS_AI = TetrisAI()

### Step 2: Create the model file

Under the same directory of `tetris_game.py` file create `tetris_model.py` and copy/paste following code.

	import random

class Shape(object):
    shapeNone = 0
    shapeI = 1
    shapeL = 2
    shapeJ = 3
    shapeT = 4
    shapeO = 5
    shapeS = 6
    shapeZ = 7

    shapeCoord = (
        ((0, 0), (0, 0), (0, 0), (0, 0)),
        ((0, -1), (0, 0), (0, 1), (0, 2)),
        ((0, -1), (0, 0), (0, 1), (1, 1)),
        ((0, -1), (0, 0), (0, 1), (-1, 1)),
        ((0, -1), (0, 0), (0, 1), (1, 0)),
        ((0, 0), (0, -1), (1, 0), (1, -1)),
        ((0, 0), (0, -1), (-1, 0), (1, -1)),
        ((0, 0), (0, -1), (1, 0), (-1, -1))
    )

    def __init__(self, shape=0):
        self.shape = shape

    def getRotatedOffsets(self, direction):
        tmpCoords = Shape.shapeCoord[self.shape]
        if direction == 0 or self.shape == Shape.shapeO:
            return ((x, y) for x, y in tmpCoords)

        if direction == 1:
            return ((-y, x) for x, y in tmpCoords)

        if direction == 2:
            if self.shape in (Shape.shapeI, Shape.shapeZ, Shape.shapeS):
                return ((x, y) for x, y in tmpCoords)
            else:
                return ((-x, -y) for x, y in tmpCoords)

        if direction == 3:
            if self.shape in (Shape.shapeI, Shape.shapeZ, Shape.shapeS):
                return ((-y, x) for x, y in tmpCoords)
            else:
                return ((y, -x) for x, y in tmpCoords)

    def getCoords(self, direction, x, y):
        return ((x + xx, y + yy) for xx, yy in self.getRotatedOffsets(direction))

    def getBoundingOffsets(self, direction):
        tmpCoords = self.getRotatedOffsets(direction)
        minX, maxX, minY, maxY = 0, 0, 0, 0
        for x, y in tmpCoords:
            if minX > x:
                minX = x
            if maxX < x:
                maxX = x
            if minY > y:
                minY = y
            if maxY < y:
                maxY = y
        return (minX, maxX, minY, maxY)


class BoardData(object):
    width = 10
    height = 22

    def __init__(self):
        self.backBoard = [0] * BoardData.width * BoardData.height

        self.currentX = -1
        self.currentY = -1
        self.currentDirection = 0
        self.currentShape = Shape()
        self.nextShape = Shape(random.randint(1, 7))

        self.shapeStat = [0] * 8

    def getData(self):
        return self.backBoard[:]

    def getValue(self, x, y):
        return self.backBoard[x + y * BoardData.width]

    def getCurrentShapeCoord(self):
        return self.currentShape.getCoords(self.currentDirection, self.currentX, self.currentY)

    def createNewPiece(self):
        minX, maxX, minY, maxY = self.nextShape.getBoundingOffsets(0)
        result = False
        if self.tryMoveCurrent(0, 5, -minY):
            self.currentX = 5
            self.currentY = -minY
            self.currentDirection = 0
            self.currentShape = self.nextShape
            self.nextShape = Shape(random.randint(1, 7))
            result = True
        else:
            self.currentShape = Shape()
            self.currentX = -1
            self.currentY = -1
            self.currentDirection = 0
            result = False
        self.shapeStat[self.currentShape.shape] += 1
        return result

    def tryMoveCurrent(self, direction, x, y):
        return self.tryMove(self.currentShape, direction, x, y)

    def tryMove(self, shape, direction, x, y):
        for x, y in shape.getCoords(direction, x, y):
            if x >= BoardData.width or x < 0 or y >= BoardData.height or y < 0:
                return False
            if self.backBoard[x + y * BoardData.width] > 0:
                return False
        return True

    def moveDown(self):
        lines = 0
        if self.tryMoveCurrent(self.currentDirection, self.currentX, self.currentY + 1):
            self.currentY += 1
        else:
            self.mergePiece()
            lines = self.removeFullLines()
            self.createNewPiece()
        return lines

    def dropDown(self):
        while self.tryMoveCurrent(self.currentDirection, self.currentX, self.currentY + 1):
            self.currentY += 1
        self.mergePiece()
        lines = self.removeFullLines()
        self.createNewPiece()
        return lines

    def moveLeft(self):
        if self.tryMoveCurrent(self.currentDirection, self.currentX - 1, self.currentY):
            self.currentX -= 1

    def moveRight(self):
        if self.tryMoveCurrent(self.currentDirection, self.currentX + 1, self.currentY):
            self.currentX += 1

    def rotateRight(self):
        if self.tryMoveCurrent((self.currentDirection + 1) % 4, self.currentX, self.currentY):
            self.currentDirection += 1
            self.currentDirection %= 4

    def rotateLeft(self):
        if self.tryMoveCurrent((self.currentDirection - 1) % 4, self.currentX, self.currentY):
            self.currentDirection -= 1
            self.currentDirection %= 4

    def removeFullLines(self):
        newBackBoard = [0] * BoardData.width * BoardData.height
        newY = BoardData.height - 1
        lines = 0
        for y in range(BoardData.height - 1, -1, -1):
            blockCount = sum([1 if self.backBoard[x + y * BoardData.width] > 0 else 0 for x in range(BoardData.width)])
            if blockCount < BoardData.width:
                for x in range(BoardData.width):
                    newBackBoard[x + newY * BoardData.width] = self.backBoard[x + y * BoardData.width]
                newY -= 1
            else:
                lines += 1
        if lines > 0:
            self.backBoard = newBackBoard
        return lines

    def mergePiece(self):
        for x, y in self.currentShape.getCoords(self.currentDirection, self.currentX, self.currentY):
            self.backBoard[x + y * BoardData.width] = self.currentShape.shape

        self.currentX = -1
        self.currentY = -1
        self.currentDirection = 0
        self.currentShape = Shape()

    def clear(self):
        self.currentX = -1
        self.currentY = -1
        self.currentDirection = 0
        self.currentShape = Shape()
        self.backBoard = [0] * BoardData.width * BoardData.height


BOARD_DATA = BoardData()

### What is shape coordinates?

	shapeCoord = (
        ((0, 0), (0, 0), (0, 0), (0, 0)),
        ((0, -1), (0, 0), (0, 1), (0, 2)),
        ((0, -1), (0, 0), (0, 1), (1, 1)),
        ((0, -1), (0, 0), (0, 1), (-1, 1)),
        ((0, -1), (0, 0), (0, 1), (1, 0)),
        ((0, 0), (0, -1), (1, 0), (1, -1)),
        ((0, 0), (0, -1), (-1, 0), (1, -1)),
        ((0, 0), (0, -1), (1, 0), (-1, -1))
    )

### What is Numpy Array?

As the name gives away, a NumPy array is a central data structure of the numpy library. The library’s name is short for “Numeric Python” or “Numerical Python”.

![](/images/numpy_array.png)

### Three dimentional array

![](/images/numpy_array_visual.gif)

### What do you expect from future classes?

### Other data visualization examples

#### Evolution of data science

![](/images/evolution_data_science.gif)

#### World climate change

![](/images/world_climate_change.gif)

### Chatbot example

![](/images/chatbot01.gif)