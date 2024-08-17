![image](https://github.com/user-attachments/assets/3aa3820b-2102-435c-9b34-d33f475eb73b)
![image](https://github.com/user-attachments/assets/d35d397d-2a6f-4089-95ed-731279e16f8f)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Snake Game 

## Overview
In this workshop, you will build a snake game from scratch, following the basic principles of Object-Oriented Programming (OOP).

## Setup
You are provided with a skeleton, which contains the following items:

- **StartUp class** – the entry point of your program.
- **Core folder** – contains the main functionality of the program.
- **Enums folder** – holds data about the snake's directions.
- **GameObjects folder** – contains the main objects of the game.
- **Utilities folder** – already written; includes information about your ConsoleWindow.

## Task 1: Structure

### Game Objects
In the `GameObjects` folder, create the following classes:

#### Point Class
- Represents the 2D space where all objects exist.
- **Properties**: 
  - `LeftX` and `TopY` - integers representing the horizontal and vertical positions of the object.
- **Methods**:
  - `Draw(symbol)` - uses `Console.SetCursorPosition` with the current point coordinates and writes the symbol on the console.
  - `Draw(leftX, topY, symbol)` - overloads the previous method.

**Constructor**: 
- Initializes `LeftX` and `TopY` with the provided values.

#### Wall Class
- Inherits from `Point` and extends its functionality.
- **Methods**:
  - `SetHorizontalLine(topY)` - iterates from zero to the current `LeftX` and draws the horizontal line with a square symbol (`\u25A0`).
  - `SetVerticalLine(leftX)` - similar to `SetHorizontalLine`, but for vertical lines.
  - `InitializeWallBorders()` - sets the horizontal and vertical lines for the four sides of the wall.

**Constructor**:
- Calls `InitializeWallBorders` to set up the wall.

#### Food Class (Abstract)
- Inherits from `Point` and implements the logic for different types of food in the game.
- **Property**:
  - `Points` - indicates the score given by each type of food.
- **Methods**:
  - `SetRandomPosition(Queue<Point> snakeParts)` - sets the position of the current food at a random place inside the wall, avoiding the snake's current position.
  - `IsFoodPoint(Point snakePosition)` - checks if the food is at the snake’s head position.
  - `Draw()` - draws the food on the console, potentially with a colorful background.

**Constructor**:
- Implements the basic setup for food items.

#### Child Classes of Food
- **FoodAsterisk**: 
  - **Symbol**: `*`
  - **Points**: 1
- **FoodDollar**:
  - **Symbol**: `$`
  - **Points**: 2
- **FoodHash**:
  - **Symbol**: `#`
  - **Points**: 3

#### Snake Class
- Manages the snake's behavior, movement, and interaction with food.
- **Fields**:
  - A queue holding all points representing the snake's body.
- **Methods**:
  - `CreateSnake()` - initializes the snake with a length of 6.
  - `GetFoods()` - initializes the food types.
  - `IsMoving(Point direction)` - controls snake movement and checks if it hits the wall or itself.
  - `GetNextPoint(Point direction)` - calculates the next position of the snake’s head based on the direction.
  - `Eat(Point direction, Point snakeHead)` - increases the snake's length after eating food and generates new food.

**Constructor**:
- Sets up the initial snake configuration.

#### Engine Class
- Manages the user interface and interactions.
- **Method**:
  - `Run()` - handles the main logic of the game, including direction input and snake movement.
  - `GetNextDirection()` - maps keyboard input to snake movement.
  - `AskUserForRestart()` - prompts the user to restart the game or exit.
  - `StopGame()` - displays "GameOver" and exits the game.

**Constructor**:
- Initializes the wall, snake, and sets up the default settings.

#### StartUp Class
- Initializes the wall, snake, and starts the game by calling the `Engine.Run()` method.

### Game Statistics
The game displays statistics on the right side of the screen. You can implement additional methods to show these statistics on the console.

Start the game and enjoy! 😊
