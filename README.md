# RaceCar_Project
Check comments if a section of code confuses you.
The car's movement is the only major problem left and you can comment out the function for drawing the finish line, i was still working on something.
commented out code you can ignore, they were just ideas i might consider implementing.
import turtle
import time
import random
turtle.shape("turtle")
#turtle.speed(100)

#increases the speed of the car after 15 seconds
'''def increaseSpeed():
    
    for timePassed in range(150):
        if timePassed%15 == 0:
            speed = speed + random.randint(1,100)
            turtle.speed(speed)
    return'''

# draws the F1 track
'''def DrawTrack():
    turtle.penup()
    turtle.color("grey") #to se coor of the track
    turtle.begin_fill() # start to colour
    turtle.ht()
    turtle.setpos(-250,-250)
    turtle.pendown()
    for i in range(1,3):
        turtle.forward(500)
        turtle.circle(250,180)
    turtle.end_fill() # stop coloring
    turtle.penup()
    turtle.color("white")
    turtle.begin_fill()
    turtle.ht()
    turtle.setpos(-150,-150)
    turtle.pendown()
    for j in range(1,3):
        turtle.forward(300)
        turtle.circle(150,180)
    turtle.end_fill()
    return'''
def drawAsquare():
    for i in range(4):
        turtle.forward(20)
        turtle.left(90)
    return

def DrawFinishLineBlack():
    position1 = -430
    for i in range(23):
        turtle.penup()
        turtle.color("black")
        turtle.begin_fill()
        turtle.setpos(position1,-54)
        position1 += 40
        turtle.pendown()
        drawAsquare()
        turtle.ht()
        turtle.end_fill()
    position2 = -450   
    for j in range(23):
        turtle.penup()
        turtle.color("black")
        turtle.begin_fill()
        turtle.setpos(position2,-34)
        position2 += 40
        turtle.pendown()
        drawAsquare()
        turtle.ht()
        turtle.end_fill()
    return
def DrawFinishLineWhite():
    position3 = -450
    for k in range(23):
        turtle.penup()
        turtle.color("white")
        turtle.begin_fill()
        turtle.setpos(position3,-54)
        position3 += 40
        turtle.pendown()
        drawAsquare()
        turtle.ht()
        turtle.end_fill()
    position4 = -430   
    for l in range(23):
        turtle.penup()
        turtle.color("white")
        turtle.begin_fill()
        turtle.setpos(position4,-34)
        position4 += 40
        turtle.pendown()
        drawAsquare()
        turtle.ht()
        turtle.end_fill()
    return

'''newTurtle1 = turtle.Turtle() #will create a new raceCar depending on user input
newTurtle1.speed(0)
newTurtle1.color("blue")
newTurtle1.shape("classic") #have to specify what shape each turtle will take
newTurtle1.penup()
newTurtle1.ht()
newTurtle1.goto(-35,-167)
newTurtle1.st()
newTurtle1.pendown()
newTurtle1.write(random.randint(1,10))

#Turtle 2
newTurtle2 = turtle.Turtle() #will create a new raceCar depending on user input
newTurtle2.speed(0)
newTurtle2.color("red")
newTurtle2.shape("classic") #have to specify what shape each turtle will take
newTurtle2.penup()
newTurtle2.ht()
newTurtle2.goto(-35,-187)
newTurtle2.st()
newTurtle2.pendown()
newTurtle2.write(random.randint(1,10))

#Turtle 3
newTurtle3 = turtle.Turtle() #will create a new raceCar depending on user input
newTurtle3.speed(0)
newTurtle3.color("orange")
newTurtle3.shape("classic") #have to specify what shape each turtle will take
newTurtle3.penup()
newTurtle3.ht()
newTurtle3.goto(-35,-207)
newTurtle3.pendown()
newTurtle3.st()
newTurtle3.write(random.randint(1,10))

#Turtle 4
newTurtle4 = turtle.Turtle() #will create a new raceCar depending on user input
newTurtle4.speed(0)
newTurtle4.color("purple")
newTurtle4.shape("classic") #have to specify what shape each turtle will take
newTurtle4.penup()
newTurtle4.ht()
newTurtle4.goto(-35,-227)
newTurtle4.st()
newTurtle4.pendown()
newTurtle4.write(random.randint(1,10))
   # return
'''
def choose_random_color():# allows the racecar to be a different color
    colors = [
        "#FF5733",  # Red
        "#33FF57",  # Green
        "#3357FF",  # Blue
        "#FFFF33",  # Yellow
        "#FF33FF",  # Magenta
        "#33FFFF",  # Cyan
        "#FFFFFF",  # White
        "#800000",  # Maroon
        "#808000",  # Olive
        "#008080",  # Teal
        "#800080",  # Purple
        "#FFA07A",  # Light Salmon
        "#20B2AA",  # Light Sea Green
        "#87CEEB",  # Sky Blue
        "#FFB6C1",  # Light Pink
        "#4682B4",  # Steel Blue
        "#D2691E",  # Chocolate
        "#FF69B4",  # Hot Pink
        "#8B4513"   # Saddle Brown
    ]
    return random.choice(colors)

#cars = []
'''def placeTheRaceCars(n):
    place= -167
    for i in range(n):
        car = turtle.Turtle() #will create a new raceCar depending on user input
        #car.speed(0)#race car starts of stationery
        car.color(choose_random_color())
        car.shape("classic") #have to specify what shape each turtle will take
        car.penup()
        car.goto(15,place)
        car.pendown()
        raceCar_number = random.randint(1,99) #generates a random number for each car
        place -= 25
        cars.append((car, raceCar_number)) #adds car object and its number to a list of cars
    return'''
#will check if the xcoordinate of the cars are the same as or less than the xcoordinate of the finish line
'''def is_x_coord_within_limit(point, limit):
    return point.x <= limit'''
'''def movementOfCars():
    initial_speed = random.randint(1,10)
    for (car, raceCar_number) in cars: #goes in the list cars an item(car) eacg iteraion and handles the movement for each car
         newCars.append(car)
         for carItem in newCars:
             for i in range(numOfCars):
                 
    return'''
def placementAndMovementOfCars(n):
    #Placement of cars
    cars = []
    raceCar_numbers = []
    speeds = []
    for i in range(n):
        car = turtle.Turtle() #will create a new raceCar depending on user input
        car.color(choose_random_color())
        car.shape("classic") #have to specify what shape each turtle will take
        car.penup()
        car.goto(10,0)
        car.left(90) #so tat the car faces the top of the screen
        car.pendown()
        
        raceCar_number = random.randint(1,99) #generates a random number for each car
        raceCar_numbers.append(raceCar_number)
        #f string that evualatees the variables or expressions in the curly brackets to give us the car and its number
        print(f"Car {i+1} has a raceCar number {raceCar_number}")
        
        initial_speed = random.randint(1,10)#generates random speed in the beginnig
        #adds initial speed to the speeds list and it becomes our current speed
        speeds.append(initial_speed)
        cars.append(car)
        
    #Movement of Cars
    #creates a lap counter for each car depending on the numOfCars eg if numOfCars i 2 laps = [0,0]
    laps = [0] * numOfCars
    start_time = time.time()#creates the current time so we can see how much time has passed
    
    while True:
        #for each car and it index in the list of cars(enumerate basically says to use both the car object and its index for each iteration)
        for i,car in enumerate(cars):
            #moves the car forward using the current speed(initial speed) stored in the speeds list.
            car.forward(speeds[i])
            car.left(10) #creates the spiral effect
            
            '''if car.xcor() == car.xcor():#checks if the the car has passed the starting postion
                laps[i] += 1#if that is true the lap counter for the current car object is incremented
                #car.goto(-450, 0)  # Reset car to starting position
                #gets the current car objects racenumber and how many laps it has completed
                print(f"Car {raceCar_numbers[i]} completed lap {laps[i]}")
                
            if time.time() - start_time > 15:# checks if the current time-initial time is > 15
                speeds[i] += random.randint(1,20) # Increase speed by a random amount
                start_time = time.time()  # Reset the time to the initial so that 15 seconds can pass again
            
            # Check if the current ac has ccompleted 20 laps if so game ends
            if laps[i] >= 20:
                #prints the number of the car that has won the race
                print(f"Car {raceCar_numbers[i]} wins the race after 20 laps!")
                window.bye()  # Closes the screen when the race ends.
                return
        window.update()'''
    return
    

#Main code
# WINDOW SETUP
window = turtle.Screen() # screen the pops up is assigned to the variable window
window.title("F1 Race") # name of the window(screen)
#window.setup(width=1000, height=800)#sets the size of the screen
window.bgcolor("grey")

numOfCars= int(input("How mant cars do you want to race(Min is 2)"))
#DrawTrack()
DrawFinishLineBlack()
DrawFinishLineWhite()
placementAndMovementOfCars(numOfCars)
#time.sleep(1) #once the cars are placed, Pauses the game for one second before the race begins

