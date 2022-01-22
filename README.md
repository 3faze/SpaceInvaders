```
import turtle as t
import math

#Screen
sc = t.Screen()
sc.bgcolor("black")
sc.title("Space Invaders")



#Border
border = t.Turtle()
border.hideturtle()
border.speed(0)
border.color("white")
border.penup()
border.setposition(-300, -300)
border.pensize(3)
border.pendown()
for side in range(4):
	border.fd(600)
	border.lt(90)
border.penup()

#Player
player = t.Turtle()
player.hideturtle()
player.color("gold")
player.shape("triangle")
player.penup()
player.speed(0)
player.setposition(0, -250)
player.setheading(90)
player.showturtle()

playerSpeed = 15

#Enemy
enemy = t.Turtle()
enemy.hideturtle()
enemy.color("red")
enemy.shape("circle")
enemy.penup()
enemy.speed(0)
enemy.setposition(-200, 250)
enemy.showturtle()

enemySpeed = 2

#Player's Weapon
bullet = t.Turtle()
bullet.hideturtle()
bullet.color("light sky blue")
bullet.shape("triangle")
bullet.penup()
bullet.speed(0)
bullet.setheading(90)
bullet.shapesize(0.5, 0.5)

bulletSpeed = 20


#Bullet State
#Ready -> Ready To Shoot
#Fire -> Already Shot A Bullet

bulletState = "Ready"

#Move Left
def move_left():
	x = player.xcor()
	x -= playerSpeed
	if x > -290:
		player.setx(x)

#Move Right
def move_right():
	x = player.xcor()
	x += playerSpeed
	if x < 290:
		player.setx(x)

#Fire
def fire_bullet():
    global bulletState
    if bulletState == "Ready":
        bulletState = "Fire"
        x = player.xcor()
        y = player.ycor()
        bullet.setposition(x, y + 10)
        bullet.showturtle()
        

#def isCollision(t1, t2):
    
	

#def isCollision2(t1, t2):
	

t.listen()
t.onkeypress(move_left, "a")
t.onkeypress(move_right, "d")
t.onkeypress(fire_bullet, "space")

#Main Loop
while True:
    sc.update()

    #Move Enemy
    x = enemy.xcor()
    x += enemySpeed
    enemy.setx(x)

    if enemy.xcor() > 290 or enemy.xcor() < -290:
        enemySpeed *= -1
        y = enemy.ycor()
        y -= 40
        enemy.sety(y)
    if bulletState == "Fire":
        y = bullet.ycor()
        y += bulletSpeed
        bullet.sety(y)
```
