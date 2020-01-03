---
title: "Ping Pong Game"
date: 2020-01-02T18:29:22+08:00
weight: 15
pre: "<b>15. </b>"
chapter: false
---

### Ping Pong Game

#### class Objectives

- Python basics summary
- Simple game design for beginners
- Object Oriented Programming in practice

#### Ping Pong game flowchart

![](/images/pong_game_design.png)

#### Building blocks

**Module**

Turtle is the only module should be imported since this game is built on the top of turtle module.

```python
import turtle
```

**Variables**

Two variables must be declared to record scores of Pddle A and Paddle B.

```python
score_a = 0
score_b = 0
```

**Objects**

- Screen

![](/images/screen.png)

```python
screen = turtle.Screen()
screen.title("Pong")
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.tracer(0)
```

- Paddle A

![](/images/paddle_a.png)

```python
paddle_a = turtle.Turtle()
paddle_a.speed(0)
paddle_a.shape("square")
paddle_a.color("white")
paddle_a.shapesize(stretch_wid=5, stretch_len=1)
paddle_a.penup()
paddle_a.goto(-350, 0)
```

- Paddle B

![](/images/paddle_b.png)

```python
paddle_b = turtle.Turtle()
paddle_b.speed(0)
paddle_b.shape("square")
paddle_b.color("white")
paddle_b.shapesize(stretch_wid=5, stretch_len=1)
paddle_b.penup()
paddle_b.goto(350, 0)
```

- Ball

![](/images/ball.png)

```python
ball = turtle.Turtle()
ball.speed(0)
ball.shape("circle")
ball.color("white")
ball.penup()
ball.goto(0, 0)
ball.dx = 0.1
ball.dy = -0.1
```

- Pen

Pen is the object to record scores that gained by Paddle A and B.

![](/images/pen.png)

```python
pen = turtle.Turtle()
pen.speed(0)
pen.color("white")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Player A: 0  Player B: 0", align="center", font=("Courier", 20, "normal"))
```

**Functions**

- Paddle A Up

![](/images/paddle_a_up.png)

```python
def paddle_a_up():
    y = paddle_a.ycor()
    y += 30
    paddle_a.sety(y)
```

- Paddle A Down

![](/images/paddle_a_down.png)

```python
def paddle_a_down():
    y = paddle_a.ycor()
    y -= 30
    paddle_a.sety(y)
```

- Paddle B Up

![](/images/paddle_b_up.png)

```python
def paddle_b_up():
    y = paddle_b.ycor()
    y += 30
    paddle_b.sety(y)
```

- Paddle B Down

![](/images/paddle_b_down.png)

```python
def paddle_b_down():
    y = paddle_b.ycor()
    y -= 30
    paddle_b.sety(y)
```

- Keyboard binding

![](/images/keyboard_binding.png)

```python
screen.listen()
screen.onkeypress(paddle_a_up, "w")
screen.onkeypress(paddle_a_down, "s")
screen.onkeypress(paddle_b_up, "Up")
screen.onkeypress(paddle_b_down, "Down")
```

#### Workflow

```python
while True:
    screen.update()

    # move the ball
    ball.setx(ball.xcor() + ball.dx)
    ball.sety(ball.ycor() + ball.dy)

    # border checking
    if ball.ycor() > 280:
        ball.sety(280)
        ball.dy *= -1

    if ball.ycor() < -280:
        ball.sety(-280)
        ball.dy *= -1

    #left and right
    if (ball.xcor() < -340 and ball.xcor() > -350) and (paddle_a.ycor() + 50 > ball.ycor() > paddle_a.ycor() - 50):
        score_a += 1
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Courier", 20, "normal"))
    if ball.xcor() > 380:
        score_a = 0
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Courier", 20, "normal"))
        ball.goto(0, 0)
        ball.dx *= -1


    if (ball.xcor() > 340 and ball.xcor() < 350) and (paddle_b.ycor() + 50 > ball.ycor() > paddle_b.ycor() - 50):
        score_b += 1
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Courier", 20, "normal"))
    if ball.xcor() < -380:
        score_b = 0
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Courier", 20, "normal"))
        ball.goto(0, 0)
        ball.dx *= -1


    # paddle and ball collisions
    if (ball.xcor() > 340 and ball.xcor() < 350) and (paddle_b.ycor() + 50 > ball.ycor() > paddle_b.ycor() - 50):
        ball.setx(340)
        ball.dx *= -1

    if (ball.xcor() < -340 and ball.xcor() > -350) and (paddle_a.ycor() + 50 > ball.ycor() > paddle_a.ycor() - 50):
        ball.setx(-340)
        ball.dx *= -1
```

#### Final effect of the Ping Pong Game

![](/images/final_effect.png)

#### Game rules

- Ping Pong is a two player game, player A on left and player B on right.
- Both player only moves up and down by pressing key 'w' and 's' for player A, key 'Up' and 'Down' for player B.
- Player who touches the ball scores one point which is recorded at the top of the game screen.
- When the ball cross the board, game starts again.

Happy coding!

Happy gaming!