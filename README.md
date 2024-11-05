# RaceCar_Project
'''
Check comments if a section of code confuses you.
I have updated the code, everything should be working only improvements are necessary now
So enjoy
'''
import turtle
import random
import time

# Set up the screen
screen = turtle.Screen()
screen.title("Formula One Car Race")
screen.bgcolor("gray")
#screen.setup(width=1000, height=800)

# Set up constants
NUMBER_OF_LAPS = 20
SPEED_INCREMENT_INTERVAL = 15  # in seconds(used to check if the current- intial time is > 15 seconds)
LAP_DISTANCE = 360  # distance for one lap in degrees

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

# Function to set up each car with properties in a dictionary
def createCars(n):
    cars = []
    for i in range(n):
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
    car["turtle"].right(2)  # Spiral effect
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

# Main function to run the race
def race(numOfCars):
    cars = createCars(numOfCars) #initializes the cars
    start_time = time.time() #initilaizes the initial time

    # Race loop
    while True:
        for car in cars:
            moveCar(car)

            # Check if any car has completed all 20 laps
            if car["lapsFinished"] >= NUMBER_OF_LAPS: #if the current cars lap counter is >= 20
                print(f"Car {car['raceCar_number']} wins the race!")
                screen.bye()#closes the screen when a car reaches 20 laps
                return  # End the game when a car wins

        # Increase each car's speed every 15 seconds
        if time.time() - start_time >= SPEED_INCREMENT_INTERVAL: #checks the current time - initial time >=15
            increaseSpeed(cars)
            start_time = time.time() #resets time to initial

# Get user input and start the race 
numOfCars = int(input("Enter the number of cars in the race: "))
race(numOfCars)  # Start the race with the provided number of cars

screen.mainloop() #s essential for maintaining the graphics window's open state and responsiveness



