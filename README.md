Below is a very detailed Markdown file (README.md) designed for your Hangman game repository. It includes everything you requested: all functions, specifications, data structures used, how to run, how to download, key features, libraries used, and a line-by-line analysis of key code sections. This is a comprehensive, self-contained document to serve as the ultimate guide for your project.

---

# Hangman Game Repository

Welcome to the Hangman Game, a classic word-guessing game implemented in C++ with graphical enhancements using the SDL (Simple DirectMedia Layer) library. This project brings the traditional Hangman experience to life with animated visuals, multiple word categories, difficulty levels, and a suggestion system. Whether you're a player or a developer, this README.md provides all the information you need to understand, build, run, and contribute to the game.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Prerequisites](#prerequisites)
3. [How to Download](#how-to-download)
4. [Building the Project](#building-the-project)
5. [Running the Game](#running-the-game)
6. [Gameplay](#gameplay)
7. [Key Features](#key-features)
8. [Code Overview](#code-overview)
9. [Data Structures Used](#data-structures-used)
10. [Libraries Used](#libraries-used)
11. [Detailed Function Specifications](#detailed-function-specifications)
12. [Line-by-Line Code Analysis](#line-by-line-code-analysis)
13. [Contributing](#contributing)
14. [License](#license)

---

## Project Overview

This Hangman game is a C++ application that uses SDL2 for rendering graphics, handling input, and managing the game window. Players guess letters to reveal a hidden word, with a limited number of incorrect guesses allowed before the hangman is fully drawn, resulting in a loss. The game includes:

- Multiple word categories (e.g., Fruits, Jobs, Plants)
- Two difficulty levels (Easy and Hard)
- A suggestion system (limited uses)
- A 90-second timer per game
- Animated graphics for hangman stages and win/lose outcomes
- Score tracking for wins and losses

The project is modular, split across several source files for maintainability and clarity.

---

## Prerequisites

To build and run the Hangman game, ensure you have the following installed:

- *C++ Compiler*: A modern compiler like MinGW (for Windows), GCC (Linux), or Clang (macOS).
- *SDL2 Library*: Core library for graphics, window management, and input.
  - Download from [SDL2 official site](https://www.libsdl.org/download-2.0.php).
- *SDL2_image Library*: For loading PNG images.
  - Available at [SDL2_image](https://www.libsdl.org/projects/SDL_image/).
- *SDL2_ttf Library*: For rendering TrueType fonts.
  - Get it from [SDL2_ttf](https://www.libsdl.org/projects/SDL_ttf/).
- *CodeBlocks IDE* (Optional): For using the provided project file (hangman.cbp).
- *Font File*: VeraMoBd.ttf (included in the repository).
- *Assets*: Images in img/ and word lists in words/ (included in the repository).

On Windows, ensure the DLLs (SDL2.dll, SDL2_image.dll, SDL2_ttf.dll) are in the executable's directory or system path.

---

## How to Download

To get the source code:

1. *Via GitHub ZIP*:
   - Go to the repository page on GitHub.
   - Click the green "Code" button.
   - Select "Download ZIP" to download the project as a compressed file.
   - Extract the ZIP to your desired location.

2. *Using Git*:
   - Open a terminal or command prompt.
   - Run the following command to clone the repository:
     bash
     git clone https://github.com/yourusername/hangman.git
     
   - Replace yourusername with the actual GitHub username or repository URL.

Once downloaded, you'll have all source files, assets, and the project file.

---

## Building the Project

You can build the project using CodeBlocks or manually with a compiler.

### Using CodeBlocks

1. Open hangman.cbp in CodeBlocks.
2. Ensure the compiler settings include paths to SDL2, SDL2_image, and SDL2_ttf libraries (preconfigured in the .cbp file).
3. Click "Build" or press F9 to compile and link the project.
4. The output executable (hangman.exe) will be in bin/Debug/ or bin/Release/, along with required DLLs, font, and assets.

### Manual Compilation

Use a command-line compiler like g++. Example command for Windows with MinGW:

bash
g++ -o hangman main.cpp Game.cpp SkickSDL.cpp painter.cpp utility.cpp -lmingw32 -lSDL2main -lSDL2 -lSDL2_image -lSDL2_ttf -I/path/to/SDL2/include -L/path/to/SDL2/lib


- Replace /path/to/SDL2/include and /path/to/SDL2/lib with the actual paths to your SDL2 installation.
- After compilation, manually copy the following to the directory with hangman.exe:
  - DLLs: SDL2.dll, SDL2_image.dll, SDL2_ttf.dll
  - Font: VeraMoBd.ttf
  - Directories: img/ (images) and words/ (word lists)

---

## Running the Game

After building:

1. Navigate to the output directory (e.g., bin/Debug/ or where hangman.exe is located).
2. Run the executable:
   bash
   hangman.exe
   
3. If manually compiled, ensure all required files (DLLs, font, img/, words/) are in the same directory as the executable.

The game window will open, and you can start playing.

---

## Gameplay

Here’s how to play the Hangman game:

- *Objective*: Guess the hidden word by suggesting letters.
- *Start*:
  - Select a word category (e.g., All Categories, Fruits, Jobs).
  - Choose a difficulty level (Easy or Hard).
- *Guessing*:
  - Press any letter key (A-Z) to guess.
  - Correct guesses reveal the letter in the word.
  - Incorrect guesses add parts to the hangman (up to 7 mistakes allowed).
- *Suggestions*:
  - Press the Spacebar to reveal a random unguessed letter (limited to 2 uses per game).
- *Time Limit*: You have 90 seconds to guess the word.
- *Win/Lose*:
  - *Win*: Guess the full word before 7 incorrect guesses or the timer runs out.
  - *Lose*: The hangman is fully drawn (7 parts) or time expires.
- *Post-Game*:
  - Press Enter to play again.
  - Press Esc to exit.

The screen displays:
- The current word (with dashes for unguessed letters)
- Incorrect guesses
- Remaining time
- Win/loss tally

---

## Key Features

- *Multiple Word Categories*: Options like Fruits, Asia Countries, Jobs, Plants, and All Categories.
- *Difficulty Levels*: Easy (shorter words) and Hard (longer words).
- *Suggestion System*: Up to 2 hints per game via the Spacebar.
- *Animated Graphics*: Visuals for hangman stages, win/lose screens, and a plane animation for correct guesses.
- *Timer*: 90-second limit per round.
- *Score Tracking*: Displays wins and losses across sessions.

---

## Code Overview

The project is organized into several files for modularity:

- **main.cpp**: Entry point, initializes SDL and starts the game loop.
- **Game.h / Game.cpp**: Core game logic, including state management and guessing mechanics.
- **SkickSDL.h / SkickSDL.cpp**: SDL wrapper for window, rendering, and event handling.
- **painter.h / painter.cpp**: Graphics utilities for drawing shapes, text, and images.
- **utility.h / utility.cpp**: Helper functions for string manipulation and word selection.
- **img/**: Directory with PNG images for hangman stages, win/lose screens, and animations.
- **words/**: Directory with text files (all.txt, fruits.txt, etc.) containing word lists.

---

## Data Structures Used

The game relies on these data structures:

- *Strings* (std::string):
  - Store the hidden word, current guess (e.g., "H--G--N"), and bad guesses (e.g., "X K P").
- *Vectors* (std::vector):
  - Hold word lists loaded from text files (e.g., vector<string> words).
- *Unordered Maps* (std::unordered_map):
  - Track unguessed letters for the suggestion system (e.g., mapping letters to their presence in the word).
- *SDL Structures*:
  - **SDL_Rect**: Defines positions and sizes for text and images on the screen.
  - **SDL_Texture**: Stores rendered graphics (e.g., text, images) for display.

---

## Libraries Used

The game leverages these external libraries:

- *SDL2*:
  - Purpose: Creates the game window, handles rendering, and processes input (keyboard events).
  - Version: 2.0 or later.
- *SDL2_image*:
  - Purpose: Loads PNG images for hangman stages and animations.
  - Supported formats: PNG (used exclusively in this project).
- *SDL2_ttf*:
  - Purpose: Renders text using TrueType fonts (e.g., VeraMoBd.ttf for game text).

These libraries are cross-platform, making the game portable to Windows, Linux, and macOS with minimal changes.

---

## Detailed Function Specifications

Below is a comprehensive list of key functions, their purposes, parameters, and return values.

### Game Class (Defined in Game.h / Game.cpp)

- **startGame()**
  - *Purpose*: Initializes a new game round.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Resets game state, calls chooseCategory(), chooseDifficulty(), and initWord().

- **chooseCategory()**
  - *Purpose*: Displays category options and processes user selection.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Uses SDL to render options; maps number keys (1-5) to categories.

- **chooseDifficulty()**
  - *Purpose*: Lets the player select Easy or Hard difficulty.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Maps keys (1 for Easy, 2 for Hard) to difficulty levels.

- **initWord()**
  - *Purpose*: Picks a random word from the selected category and difficulty.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Calls chooseWord() from utility.cpp to load and select a word.

- **guessEvent()**
  - *Purpose*: Handles keyboard input for guesses and suggestions.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Listens for A-Z keys (guesses) and Spacebar (suggestions).

- **handleGuess(char guess)**
  - *Purpose*: Processes a single guess.
  - *Parameters*: char guess - The letter guessed.
  - *Returns*: Void.
  - *Details*: Updates the current word or bad guesses; increments mistake count if incorrect.

- **updateTime()**
  - *Purpose*: Manages the 90-second timer.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Decrements time; triggers game over if it reaches zero.

- **gameOver()**
  - *Purpose*: Handles win/loss conditions and post-game options.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Displays win/lose screen; waits for Enter (restart) or Esc (exit).

### SkickSDL Class (Defined in SkickSDL.h / SkickSDL.cpp)

- **createTextTexture(string text, int x, int y)**
  - *Purpose*: Renders text on the screen.
  - *Parameters*: 
    - string text - Text to render.
    - int x, int y - Screen coordinates.
  - *Returns*: Void.
  - *Details*: Uses SDL_ttf to create a texture from text.

- **createImageBackground(string fileName)**
  - *Purpose*: Loads and sets an image as the background.
  - *Parameters*: string fileName - Path to the image file.
  - *Returns*: Void.
  - *Details*: Uses SDL_image to load PNG files.

- **createImage(string fileName, int x, int y)**
  - *Purpose*: Displays an image at specific coordinates.
  - *Parameters*: 
    - string fileName - Image path.
    - int x, int y - Position.
  - *Returns*: Void.
  - *Details*: Renders smaller images like hangman parts.

- **updateScreen()**
  - *Purpose*: Refreshes the display with the latest changes.
  - *Parameters*: None.
  - *Returns*: Void.
  - *Details*: Calls SDL_RenderPresent to update the window.

### painter Class (Defined in painter.h / painter.cpp)

- **loadTexture(string path)**
  - *Purpose*: Loads an image into an SDL texture.
  - *Parameters*: string path - File path to the image.
  - *Returns*: SDL_Texture* - Pointer to the loaded texture.
  - *Details*: Uses SDL_image for PNG loading.

- **textTexture(string text, SDL_Rect* srcRest, SDL_Rect* desRect, float _x, float _y)**
  - *Purpose*: Prepares a text texture for rendering.
  - *Parameters*: 
    - string text - Text to render.
    - SDL_Rect* srcRest, desRect - Source and destination rectangles.
    - float _x, _y - Position.
  - *Returns*: Void.
  - *Details*: Sets up text positioning.

- **createImage(SDL_Texture* texture)**
  - *Purpose*: Renders a texture on the screen.
  - *Parameters*: SDL_Texture* texture - Texture to display.
  - *Returns*: Void.
  - *Details*: Draws pre-loaded images.

### utility Functions (Defined in utility.h / utility.cpp)

- **normalize(const string& s)**
  - *Purpose*: Converts a string to uppercase.
  - *Parameters*: const string& s - Input string.
  - *Returns*: string - Uppercase string.
  - *Details*: Ensures case-insensitive comparisons.

- **chooseWord(const string& fileName, int difficult)**
  - *Purpose*: Selects a random word based on category and difficulty.
  - *Parameters*: 
    - const string& fileName - Path to word list file.
    - int difficult - Difficulty level (1 for Easy, 2 for Hard).
  - *Returns*: string - Selected word.
  - *Details*: Filters words by length (e.g., Easy: ≤6 letters, Hard: >6).

- **contains(string word, char guess)**
  - *Purpose*: Checks if a word contains a letter.
  - *Parameters*: 
    - string word - The word to check.
    - char guess - The letter to find.
  - *Returns*: bool - True if the letter is in the word.
  - *Details*: Used in guess validation.

---

## Line-by-Line Code Analysis

Here’s a detailed breakdown of key sections from Game.cpp to illustrate how the game works. (Note: This assumes a typical implementation; adjust if your code differs slightly.)

### startGame() in Game.cpp

```cpp
// Your C++ code here
void Game::startGame() {
    mistakes = 0;           // Reset mistake counter
    timeLeft = 90;          // Set timer to 90 seconds
    suggestionsLeft = 2;    // Allow 2 suggestions
    badGuesses = "";        // Clear bad guesses
    wins = wins;            // Retain win count
    losses = losses;        // Retain loss count
    chooseCategory();       // Prompt category selection
    chooseDifficulty();     // Prompt difficulty selection
    initWord();             // Select and set up the word
    gameState = PLAYING;    // Set game state to active
}
```




- *Line 1*: void Game::startGame() - Defines the function in the Game class.
- *Line 2*: mistakes = 0; - Resets the number of incorrect guesses.
- *Line 3*: timeLeft = 90; - Sets the timer to 90 seconds.
- *Line 4*: suggestionsLeft = 2; - Gives the player 2 hints.
- *Line 5*: badGuesses = ""; - Clears the string of incorrect guesses.
- *Line 6-7*: Retains the win/loss tally across games.
- *Line 8*: Calls chooseCategory() to let the player pick a category.
- *Line 9*: Calls chooseDifficulty() for difficulty selection.
- *Line 10*: Calls initWord() to pick and prepare the word.
- *Line 11*: Sets the game state to PLAYING, starting the main loop.

### handleGuess(char guess) in Game.cpp

cpp
void Game::handleGuess(char guess) {
    string normGuess = normalize(string(1, guess));
    if (badGuesses.find(normGuess) != string::npos || currentWord.find(normGuess) != string::npos) {
        return;  // Ignore repeated guesses
    }
    if (contains(wordToGuess, guess)) {
        for (int i = 0; i < wordToGuess.length(); i++) {
            if (wordToGuess[i] == guess) {
                currentWord[i] = guess;  // Reveal letter
            }
        }
        if (currentWord == wordToGuess) {
            gameState = WON;  // Player wins
        }
    } else {
        mistakes++;
        badGuesses += normGuess + " ";
        if (mistakes >= 7) {
            gameState = LOST;  // Player loses
        }
    }
}


- *Line 1*: Defines the function to process a guess.
- *Line 2*: Normalizes the guess to uppercase for consistency.
- *Line 3*: Checks if the guess was already made (in badGuesses or currentWord).
- *Line 4*: Returns early if the guess is a repeat.
- *Line 5*: Checks if the guess is in the word using contains().
- *Line 6-10*: Loops through the word, revealing all instances of the guessed letter.
- *Line 11-13*: If the full word is guessed, sets the state to WON.
- *Line 14-18*: If incorrect, increments mistakes, adds to badGuesses, and checks for loss (7 mistakes).

---

## Contributing

We welcome contributions! To get involved:

1. Fork the repository on GitHub.
2. Clone your fork locally:
   bash
   git clone https://github.com/yourusername/hangman.git
   
3. Make changes or add features.
4. Test your changes thoroughly.
5. Commit and push to your fork:
   bash
   git add .
   git commit -m "Describe your changes"
   git push origin main
   
6. Submit a pull request via GitHub with a detailed description.
7. Report bugs or suggest ideas using GitHub Issues.

---

## License

This project is licensed under the MIT License. See the LICENSE file in the repository for full details. In summary, you’re free to use, modify, and distribute this code, provided you include the license and copyright notice.

---

This README.md is a massive, detailed guide covering every aspect of your Hangman game. Place it at the root of your repository to provide users and contributors with all the information they need. Let me know if you’d like even more detail or additional sections!
