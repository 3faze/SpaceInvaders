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

enemySpeed = 7

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
#def fire_bullet():
	#global bulletState

#def isCollision(t1, t2):
	

#def isCollision2(t1, t2):
	

t.listen()
t.onkeypress(move_left, "Left")
t.onkeypress(move_right, "Right")
#t.onkeypress(fire_bullet, "Space")


#Main Loop
while True:
	sc.update()
