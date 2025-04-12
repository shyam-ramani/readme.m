# 🎮 Hangman Game Repository

# 🎮 Ultimate Hangman Game

Welcome to the **Ultimate Hangman Game** – a classic word-guessing challenge powered by **SDL2 graphics** and modern **C++**! 🎮

Dive into a visually rich, interactive experience where every guess brings your game to life. Whether you're here to play or learn, this project blends fun and coding magic through clean object-oriented design and smooth graphics.

🎯 **Guess letters. Save the stickman. Beat the clock.**  
**Ready to code, play, and level up? Let’s go! 🚀**


---


## 📋 Table of Contents

1. [🌟 Project Overview](#-project-overview)
2. [⚙️ Prerequisites](#️-prerequisites)
3. [📥 How to Download](#-how-to-download)
4. [🔨 Building the Project](#-building-the-project)
5. [🚀 Running the Game](#-running-the-game)
6. [🎮 Gameplay](#-gameplay)
7. [✨ Key Features](#-key-features)
8. [🧠 Code Overview](#-code-overview)
9. [🗂️ Data Structures Used](#️-data-structures-used)
10. [📚 Libraries Used](#-libraries-used)
11. [🔍 Detailed Function Specifications](#-detailed-function-specifications)
12. [👩💻 Line-by-Line Code Analysis](#-line-by-line-code-analysis)
13. [🤝 Contributing](#-contributing)
14. [📜 License](#-license)

---

## 🌟 Project Overview

## 🎥 Visual Showcase & Interactive Demos 🎮

![Hangman Demo](img/demo.gif) *Example gameplay (replace with actual GIF path)*

This Hangman game isn’t just about guessing words – it’s an **immersive experience**! Built in C++ with SDL2, it features:

- 🎨 **Animated graphics** (watch the hangman being drawn stroke by stroke!).
- 🌍 **Multiple categories** (Fruits 🍎, Countries 🌏, Jobs 👨⚕️, Plants 🌿).
- ⚡ **Two difficulty modes** (Easy for kids, Hard for pros!).
- 💡 **Smart suggestions** (stuck? Get a hint!).
- ⏳ **90-second timer** (race against time!).
- 📊 **Score tracking** (brag about your wins!).

**Code Structure**:
```
📁 hangman/
├── 📄 main.cpp          # Game loop & SDL initialization
├── 📄 Game.h/cpp        # Core logic (guesses, win/lose states)
├── 📄 SkickSDL.h/cpp    # SDL wrappers (rendering, events)
├── 📄 painter.h/cpp     # Drawing utilities (text, images)
├── 📄 utility.h/cpp     # Helpers (word selection, string ops)
├── 📁 img/              # All images (PNGs for hangman stages)
└── 📁 words/            # Word lists (all.txt, fruits.txt, etc.)
```

---

## ⚙️ Prerequisites

Before diving in, ensure you have:

| Tool/Library | Purpose | Installation Guide |
|--------------|---------|--------------------|
| **C++ Compiler** (GCC/MinGW) | Compile the code | [Windows](https://mingw-w64.org/) / [Linux](https://gcc.gnu.org/) / [macOS](https://clang.llvm.org/) |
| **SDL2** | Graphics & input | `sudo apt-get install libsdl2-dev` (Linux) |
| **SDL2_image** | Load PNGs | `sudo apt-get install libsdl2-image-dev` |
| **SDL2_ttf** | Render text | `sudo apt-get install libsdl2-ttf-dev` |
| **VeraMoBd.ttf** | Font file | Included in the repo 🎉 |

💡 **Windows Users**: Place SDL2 DLLs (`SDL2.dll`, `SDL2_image.dll`, `SDL2_ttf.dll`) in the same folder as your executable!

---

## 📥 How to Download

### Option 1: GitHub ZIP
1. Go to the repo ➡️ Click **Code** ➡️ **Download ZIP**.
2. Extract the ZIP 🗜️ to your preferred folder.

### Option 2: Git Clone (for devs)
```bash
git clone https://github.com/yourusername/hangman.git
cd hangman
```

---

## 🔨 Building the Project

### 🛠️ Using CodeBlocks (Recommended)
1. Open `hangman.cbp`.
2. Click **Build** (🛠️) ➡️ Executable is generated in `bin/Debug/`.

### 💻 Manual Compilation (Terminal)
```bash
g++ -o hangman main.cpp Game.cpp SkickSDL.cpp painter.cpp utility.cpp \
-lSDL2 -lSDL2_image -lSDL2_ttf
```
**⚠️ Troubleshooting**:
- **Missing Libraries?** Double-check include paths with `-I/path/to/SDL2/include`.
- **Linker Errors?** Ensure `-L/path/to/SDL2/lib` points to your SDL2 `.lib` files.

---

## 🚀 Running the Game

```bash
./hangman   # Linux/macOS
hangman.exe # Windows
```

**Expected Output**:
```
✅ Window initialized (800x600)
✅ Font loaded: VeraMoBd.ttf
🎮 Game started! Choose a category...
```

💣 **Common Errors**:
- **"Failed to load image!"**: Ensure the `img/` folder exists with PNGs.
- **Black screen?** Check if `VeraMoBd.ttf` is in the working directory.

---

## 🎮 Gameplay

**Controls**:
- 🅰️-🇿: Guess a letter.
- ␣ (Spacebar): Use a hint (2/game).
- ⏎ (Enter): Restart after game over.
- ⎋ (Esc): Quit anytime.

**Game Flow**:
1. **Choose Category** (1-5 keys):
   - `1`: All Categories 🌐
   - `2`: Fruits 🍌
   - ...etc.
2. **Select Difficulty**:
   - `1`: Easy (words ≤6 letters).
   - `2`: Hard (words >6 letters).
3. **Guess Wisely**:
   - Correct guess: Letter revealed ✨.
   - Wrong guess: Hangman grows 😱.
4. **Win/Lose**:
   - 🏆 Win: Guess the word before 7 mistakes.
   - 💀 Lose: Hangman completed or time runs out.

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| **Multi-Category Support** | Switch between 5+ themes 🎭 |
| **Dynamic Difficulty** | Easy for casuals, Hard for pros 🧠 |
| **Hint System** | Spacebar reveals a letter (limited uses) 💡 |
| **Animated UI** | Smooth transitions for hangman stages 🎨 |
| **Persistent Scores** | Wins/losses saved across sessions 💾 |

---

## 🧠 Code Overview

### 🕹️ `main.cpp`
- **Entry Point**: Initializes SDL, runs the game loop.
```cpp
int main() {
    SkickSDL sdl; // Initialize SDL
    Game game;     // Create game instance
    while (game.isRunning()) {
        game.handleEvents(); // Process input
        game.update();       // Update timer/game state
        game.render();      // Draw everything
    }
    return 0;
}
```

### 🎲 `Game.cpp`
- **Core Logic**: Manages guesses, win/lose conditions.
```cpp
void Game::handleGuess(char guess) {
    if (alreadyGuessed(guess)) return; // Ignore repeats
    if (wordContains(guess)) {
        revealLetter(guess); // Update currentWord
        checkWin();          // Does currentWord == wordToGuess?
    } else {
        addMistake();       // Increment mistakes
        checkLoss();         // If mistakes >=7, game over
    }
}
```

---

## 🗂️ Data Structures Used

### `std::vector<string> words`
- **Purpose**: Stores word lists loaded from text files.
```cpp
// Load all words from "words/fruits.txt"
vector<string> fruits = loadWords("words/fruits.txt");
```

### `std::unordered_map<char, bool> unguessedLetters`
- **Purpose**: Track letters not yet guessed for hints.
```cpp
for (char c : wordToGuess) {
    unguessedLetters[c] = false; // Initialize all as unguessed
}
```

---

## 📚 Libraries Used

| Library | Role | Why Chosen? |
|---------|------|-------------|
| **SDL2** | Window/Input | Lightweight, cross-platform 🖥️ |
| **SDL2_image** | PNG Loading | Supports transparency (for hangman PNGs) 🖼️ |
| **SDL2_ttf** | Font Rendering | Crisp text for UI 🅰️ |

---

## 🔍 Detailed Function Specifications

### `SkickSDL::createImageBackground()`
```cpp
/**
 * Loads a full-screen background image.
 * @param fileName Path to PNG (e.g., "img/background.png").
 * @throws SDL_Exception if image fails to load.
 */
void SkickSDL::createImageBackground(string fileName);
```

### `utility::chooseWord()`
```cpp
/**
 * Selects a random word from a category file.
 * @param fileName Path to word list.
 * @param difficulty 1 (Easy) or 2 (Hard).
 * @return A word meeting the length criteria.
 */
string chooseWord(const string& fileName, int difficulty);
```

---

## 👩💻 Line-by-Line Code Analysis

### `Game::updateTime()` (Timer Logic)
```cpp
void Game::updateTime() {
    Uint32 currentTime = SDL_GetTicks() / 1000; // Get current time in seconds
    if (currentTime - startTime >= 1) {         // 1 second elapsed
        timeLeft--;
        startTime = currentTime;
        if (timeLeft <= 0) {
            gameState = LOST; // Time's up! 💀
        }
    }
}
```
- **Line 2**: `SDL_GetTicks()` returns milliseconds since start.
- **Line 3**: Checks if a full second has passed.
- **Line 4-7**: Decrement `timeLeft`, trigger loss if 0.

---

## 🤝 Contributing

**First time contributing?** Here’s how:
1. 🍴 Fork the repo.
2. 🌱 Create a branch: `git checkout -b feature/amazing-feature`.
3. 💻 Code your changes.
4. 📝 Test thoroughly – no broken builds! 🚫🐛
5. 🔀 Submit a pull request. We’ll review it faster than you can say "Hangman"! ⚡

---

# 🌟 What I Learned 🌟

Building this Hangman game was like crafting a masterpiece from scratch—I went from basic code-slinger to game-dev wizard! ✨ Before this, I knew my way around C++ and some trusty data structures (arrays, vectors, stacks, and more). But this project? It was a full-on skill explosion. Here’s the dazzling rundown of what I conquered:

## 🎨 New Powers Gained 🎨

### 🏰 Object-Oriented Magic
- **What**: Mastered classes and objects in C++.
- **How**: Built `Game`, `SkickSDL`, and `Painter` classes to rule the code kingdom.
- **Why It Rocks**: Learned encapsulation (hiding the mess) and modularity (snap-together code blocks). Goodbye, spaghetti scripts—hello, elegant systems! 🛠

### 🖼 SDL Graphics Sorcery
- **What**: Conquered the SDL library for visuals and controls.
- **How**: Drew windows, shapes, and handled keyboard spells (A-Z guesses, anyone?).
- **Why It Rocks**: Turned lifeless code into a living, breathing game. My screen’s now a canvas! 🎮

### 📜 File I/O Wizardry
- **What**: Unlocked reading text files in C++.
- **How**: Loaded word lists (Fruits 🍇, Animals 🐘) to mix up the game.
- **Why It Rocks**: My game’s dynamic now—data flows like magic from files to fun! 📂

### ✂ String Alchemy
- **What**: Became a pro at string manipulation.
- **How**: Tweaked `_ _ _ _` into `H A _ _`, tracked guesses, and tamed wild letters.
- **Why It Rocks**: Words bend to my will—Hangman’s core is mine to command! 🔠

### ⚡ Event Mastery
- **What**: Captured real-time inputs with SDL’s event system.
- **How**: Made A-Z keys guess letters and Spacebar drop hints.
- **Why It Rocks**: The game reacts instantly—players feel the power! ⌨

### 🧠 Game Logic Brilliance
- **What**: Designed a brainy game flow.
- **How**: Tracked 7 wrong guesses, flipped win/lose states, kept it all smooth.
- **Why It Rocks**: Rules run like clockwork—pure gaming bliss! ⏳

### 🛡 Error-Proof Armor
- **What**: Added shields against crashes.
- **How**: Handled missing files and odd inputs with grace.
- **Why It Rocks**: My game’s tough as nails and kind to players! 🚑

## 🌠 Epic Transformation
- **Started With**: Basic C++ and simple data tricks.
- **Now**: Crafting interactive games with graphics, files, and flair!
  
This wasn’t just a project—it was a quest. I’ve leveled up big time, and I’m ready to conquer my next coding adventure! 🚀

---
## 📜 License

MIT License © 2023 YourName

```text
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```
**Made with ❤️ by [TEAM_CODE_KNIGHT]**  
[![GitHub Stars].(https://github.com/shyam-ramani/Hangman.git).  
🌟 **Star this repo if you love it!** 🌟
---
## ❓ Frequently Asked Questions (FAQ)

---

### 🔹 Q3: How can I add my own word categories?
**A:** Easy!  
1. Create a `.txt` file in the `words/` folder (e.g., `sports.txt`).  
2. Add **one word per line**.  
3. Update the game logic in `utility.cpp` to include your new category.

---

### 🔹 Q4: Can I customize the hangman images or use different themes?
**A:** Yes! Replace the `.png` files in the `img/` folder with your own images.  
Make sure:  
- Filenames remain consistent (`stage0.png` to `stage7.png`).  
- Image dimensions are similar to avoid layout issues.

---

### 🔹 Q6: Is there a Windows build of this game?
**A:** Not by default, but you can build it easily:
- Install **CodeBlocks with MinGW** or use **Visual Studio**.
- Copy required **DLLs** (like SDL2.dll, SDL2_ttf.dll, etc.) into your project directory.
- Build and run like normal!

---

### 🔹 Q7: Can I contribute to this project?
**A:** Absolutely! We love contributions.  
Here’s how to get started:
1. **Fork** the repository.  
2. Create a **new branch** for your feature or fix.  
3. Make your changes.  
4. Submit a **pull request** – we’ll review and merge it if all looks good!

---

### 🔹 Q8: Is this beginner-friendly for learning C++ and SDL2?
**A:** Totally!  
This project is great for:
- **C++ beginners** with basic class and function knowledge.
- Developers wanting to explore **SDL2**, **game loops**, and **event-driven design**.  
You’ll learn about **OOP**, **event handling**, and **graphics rendering** along the way.

---

### 🔹 Q9: What platforms does this run on?
**A:**
- ✅ **Linux** (tested on Ubuntu & Arch)
- ✅ **Windows** (via CodeBlocks or terminal with MinGW)
- ⚠️ **macOS** (supported with `brew` and some minor tweaks)

---

### 🔹 Q10: Can I turn this into a GUI app with buttons and mouse controls?
**A:** Yes!  
SDL2 supports mouse interactions. You’d need to:
- Handle `SDL_MOUSEBUTTONDOWN` events.
- Create clickable zones using `SDL_Rect`.

This is an awesome next step if you want to **expand** the project with a full GUI.

---

This version adds emojis for visual flair, clearer code examples, troubleshooting tips, and even a mock GIF placeholder. It’s designed to be engaging while maintaining technical depth! 🚀
