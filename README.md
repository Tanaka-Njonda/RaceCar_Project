import turtle
import random
import time

# Sets up the background for the race cars
screen = turtle.Screen()
screen.title("Formula One Car Race")
screen.bgcolor("gray")
#screen.setup(width=1000, height=800)

NUMBER_OF_LAPS = 20
SPEED_INCREMENT_INTERVAL = 15  # in seconds(used to check if the current- intial time is > 15 seconds)
LAP_DISTANCE = 360  # distance for one lap in degrees

def choose_random_color():# allows the racecar to be a different color chosen randomly
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

# Function to set up each car with properties in a dictionary
def createCars(numOfCars):
    cars = []
    for i in range(numOfCars):
        #create a dictonary to store all the information of each car
        car_data = {
            "turtle": turtle.Turtle(),                   # Creates a turtle object for each car
            "raceCar_number": random.randint(100, 999),    # generates random racecar number
            "speed": random.randint(1, 5),               # generate random initial speed
            "lapsFinished": 0,                         # will help to check how many laps were completed
            "angle": 0                                   # Tracks distance the car has traveled in degrees
        }
        car_data["turtle"].shape("turtle") 
        car_data["turtle"].color(choose_random_color())
        car_data["turtle"].penup()
        car_data["turtle"].goto(-300 + i * 100, 0)       # Positioning each car such that there is an equal space between them
        car_data["turtle"].pendown()

        print(f"Car {car_data['raceCar_number']} starting with speed {car_data['speed']}")
        cars.append(car_data) #stores each car and its attributes at the end of the list
    return cars #returns a list of cars

# Function to move each car in a spiral-like path and update laps
def moveCar(car):
    car["turtle"].forward(car["speed"]) # moves the car at the initial speed
    car["turtle"].right(5)  # Spiral effect
    car["angle"] += car["speed"] #updating the distance traveled by the car

    # Checks if the car has completed a lap
    if car["angle"] >= LAP_DISTANCE: #if distance travled is the same as the distance of one lap
        car["lapsFinished"] += 1 #increment the number of laps finished by one
        car["angle"] = 0 #reset the distance travelled to zero
        print(f"Car {car['raceCar_number']} completed lap {car['lapsFinished']}")

# Function to increase each car's speed
def increaseSpeed(cars):
    for car in cars:
        car["speed"] += random.randint(1,5) #increases the initial speed of each car by one
    print("Increasing speed for all cars.")

def DrawARectangle():
    for i in range(2):
        turtle.forward(50)
        turtle.right(90)
        turtle.forward(100)
        turtle.right(90)
    return
#to create the starting light
'''def DrawDifferentLights():
    x = 70
    for i in range(5):
        turtle.speed(60)
        turtle.color("black")
        turtle.begin_fill()
        turtle.penup()
        turtle.ht()
        turtle.goto(x,350)
        turtle.pendown()
        DrawARectangle()
        turtle.end_fill()
        x -= 60
    return'''

def DrawACircle():
    turtle.circle(17,360)
    return

#Function for the starting lights
def startingLights():
    xn = 70
    for h in range(5):
        turtle.speed(900)
        turtle.color("black")
        turtle.begin_fill()
        turtle.penup()
        turtle.ht()
        turtle.goto(xn,350)
        turtle.pendown()
        DrawARectangle()
        turtle.end_fill()
        xn -= 60
    x1 = -145
    for i in range(5):
        turtle.speed(50)
        turtle.penup()
        turtle.ht()
        turtle.goto(x1,255)
        turtle.color("red")
        turtle.begin_fill()
        turtle.pendown()
        DrawACircle()
        turtle.end_fill()
        x1 += 60
        time.sleep(1)
    time.sleep(1)
    x2 = -145
    for j in range(5):
        turtle.speed(50)
        turtle.penup()
        turtle.ht()
        turtle.goto(x2,300)
        turtle.color("green")
        turtle.begin_fill()
        turtle.pendown()
        DrawACircle()
        turtle.end_fill()
        x2 += 60
        time.sleep(1)

def removeStartingLights(): #will remove the starting lights after the last green light hits
    xn = 70
    for h in range(5):
        turtle.speed(900)
        turtle.color("grey")
        turtle.begin_fill()
        turtle.penup()
        turtle.ht()
        turtle.goto(xn,350)
        turtle.pendown()
        DrawARectangle()
        turtle.end_fill()
        xn -= 60
    return

# Main function to run the race
def race(numOfCars):
    cars = createCars(numOfCars) #initializes the cars
    user_bet = screen.textinput(title = "F1 Race", prompt = "Which race car will win?") #opens a window on the screen to take the users bet
    startingLights() #place starting lights beore cars moves
    removeStartingLights()
    start_time = time.time() #initilaizes the initial time

    # Race loop
    while True:
        for car in cars:
            moveCar(car)

            # Check if any car has completed all 20 laps
            if car["lapsFinished"] >= NUMBER_OF_LAPS: #if the current cars lap counter is >= 20
                print(f"Car {car['raceCar_number']} wins the race!")
                if user_bet == f"Car {car['raceCar_number']}":#will check if the users is the same as the number of the car that wins the race
                    print("Congratulations, you just became a millionaire")
                else:
                    print("So close, maybe next time lol")
                screen.bye()#closes the screen when a car reaches 20 laps
                return  # End the game when a car wins

        # Increase each car's speed every 15 seconds
        if time.time() - start_time >= SPEED_INCREMENT_INTERVAL: #checks the current time - initial time >=15
            increaseSpeed(cars)
            start_time = time.time() #resets time to initial

# initialize the starting lights, take user input and start the race
numOfCars = int(input("Enter the number of cars in the race: "))
#DrawDifferentLights()
#startingLights()
race(numOfCars)  # Start the race with the provided number of cars

screen.mainloop()
