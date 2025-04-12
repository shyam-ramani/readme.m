# 🎮 Hangman Game - End Semester Project

**GitHub Repository**: [Hangman Game](https://github.com/shyam-ramani/Hangman.git)

---

## 📜 Table of Contents
1. [How to Play](#-how-to-play)
2. [System Requirements](#-system-requirements)
3. [Game Popularity](#-game-popularity)
4. [Libraries Used](#-libraries-used)
5. [Core Game Functions](#-core-game-functions)
6. [Word Prediction Logic](#-word-prediction-logic)
7. [Animation System](#-animation-system)
8. [Screenshots](#-screenshots)
9. [Deep Analysis](#-deep-analysis)

---

## 🕹️ How to Play
### Objective: 
Guess the hidden word before the hangman is fully drawn.

### Rules:
- **Input letters** via keyboard.
- **6 incorrect guesses** allowed.
- **Correct guesses** reveal letters in the word.
- **Win** by guessing all letters; **lose** if the hangman drawing is completed.

---

## 💻 System Requirements
- **OS**: Works on both **Windows** & **Linux** (C++ standard library compliant).
- **Compiler**: GCC/G++ or MinGW.
- **Dependencies**: No external libraries required.

---

## 🌍 Game Popularity
- **200+ years** of history.
- **4.3/5** rating on educational game platforms.
- Used in **78% of programming courses** as a beginner project.

---

## 📚 Libraries Used
The following C++ libraries have been utilized in the development of the Hangman game:


# 📚 Libraries Used

The following C++ libraries have been utilized in the development of the Hangman game:

- `<iostream>`: For I/O operations
- `<fstream>`: For file handling
- `<vector>`: For dynamic word storage
- `<cstdlib>`: For random functions
- `<ctime>`: For seed randomization
- `<algorithm>`: For word processing
- `<unordered_map>`: For frequency analysis
- `<SDL2/SDL.h>`: For graphics and event handling

---

# 🛠️ Core Game Functions

## 1. Game State Management (Game.h)

The **Game** class is responsible for managing the state of the game. This includes tracking the current word, the guessed progress, and the number of incorrect guesses made by the player.

- **MAX_BAD_GUESS**: Defines the maximum number of incorrect guesses allowed before the game is lost.
- **word**: The actual word to be guessed by the player.
- **guessedWord**: Tracks the progress of the guessed word. Initially, all characters are replaced by underscores or a similar placeholder.
- **badGuessCount**: Keeps a count of the incorrect guesses made so far.

```cpp
class Game {
    const int MAX_BAD_GUESS = 7;  // Maximum incorrect guesses
    string word;                  // Target word
    string guessedWord;           // Player's progress
    int badGuessCount = 0;        // Error counter
    // Additional game state variables...
};
