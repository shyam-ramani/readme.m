# Hangman Game with SDL

## Overview
This document provides a comprehensive overview of a Hangman game implemented using the SDL (Simple DirectMedia Layer) library. The game allows players to guess a word by suggesting letters within a certain time limit. The game features categories, difficulty levels, and animations to enhance the user experience.

## Table of Contents
- [Game Structure](#game-structure)
- [Key Components](#key-components)
  - [Game Class](#game-class)
  - [SkickSDL Class](#skicksdl-class)
  - [Painter Class](#painter-class)
  - [Utility Functions](#utility-functions)
- [Game Flow](#game-flow)
- [Animation](#animation)
- [Building and Running the Game](#building-and-running-the-game)
- [Conclusion](#conclusion)

## Game Structure
The game is structured into several classes, each responsible for different aspects of the game:

- **Game**: Manages the game logic, including word selection, guessing, and game state.
- **SkickSDL**: A wrapper around SDL for easier rendering and event handling.
- **Painter**: Handles drawing shapes and text on the screen.
- **Utility Functions**: Provides helper functions for word selection and string manipulation.

## Key Components

### Game Class
The `Game` class is the core of the Hangman game. It contains methods for starting the game, choosing categories and difficulties, handling guesses, and rendering the game state.

#### Key Methods
- `startGame()`: Initializes the game state and prompts the player to choose a category and difficulty.
- `chooseCategory()`: Allows the player to select a word category.
- `chooseDifficulty()`: Allows the player to select the difficulty level.
- `guessEvent()`: Handles player input for guessing letters.
- `handleGuess()`: Processes the player's guess and updates the game state.
- `gameOver()`: Displays the game over screen and updates win/loss statistics.

### SkickSDL Class
The `SkickSDL` class simplifies the use of SDL for rendering graphics and handling events.

#### Key Methods
- `createTextTexture()`: Renders text on the screen.
- `createImageBackground()`: Sets a background image for the game.
- `updateScreen()`: Updates the display to show the current frame.

### Painter Class
The `Painter` class provides methods for drawing shapes and images on the screen.

#### Key Methods
- `createCircle()`: Draws a circle.
- `createSquare()`: Draws a square.
- `loadTexture()`: Loads an image texture from a file.

### Utility Functions
Utility functions are used for common tasks such as normalizing strings and selecting random words from a file.

#### Key Functions
- `normalize()`: Converts a string to uppercase.
- `chooseWord()`: Selects a random word from a specified category file.
- `contains()`: Checks if a character is present in a string.

## Game Flow

1. **Initialization**: The game initializes the SDL window and loads the font.
2. **Start Game**: The player starts a new game, chooses a category, and selects a difficulty level.
3. **Gameplay Loop**: The game enters a loop where it:
   - Renders the current game state.
   - Waits for player input.
   - Processes guesses and updates the game state.
4. **Game Over**: When the game ends, the player is shown the results and can choose to play again or exit.

## Animation

The game includes animations for visual feedback when a player guesses a letter correctly or incorrectly. For example, when a player guesses a letter that is in the word, a plane flies across the screen to celebrate the correct guess.

### Animation Implementation
- `renderPlane()`: Animates a plane moving across the screen.
- `planeEvent()`: Handles events during the animation, allowing the player to skip the animation by pressing the spacebar.

## Building and Running the Game

To build and run the game, follow these steps:

1. **Install SDL**: Ensure that SDL2, SDL2_image, and SDL2_ttf are installed on your system.
2. **Set Up Project**: Use a project file (like Code::Blocks) to manage the source files and dependencies.
3. **Compile**: Build the project using the provided makefile or IDE settings.
4. **Run**: Execute the compiled binary to start the game.

## Conclusion

This Hangman game demonstrates the use of SDL for creating interactive applications. The game structure is modular, allowing for easy modifications and enhancements. The combination of gameplay mechanics, user input handling, and animations provides an engaging experience for players.

This markdown document serves as a comprehensive guide to understanding the Hangman game implementation using SDL. It covers the essential components, game flow, and animation details, providing a clear overview for anyone interested in game development with SDL.
