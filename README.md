# 🎮 Hangman Game 

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![SDL2](https://img.shields.io/badge/SDL-2.0-blue.svg)](https://www.libsdl.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey.svg)](https://github.com/yourusername/hangman)

A classic word-guessing game with modern graphics powered by SDL2. Features multiple categories, difficulty levels, and a hint system!

![Hangman Screenshot](img/screenshot.png) <!-- Add a screenshot here if available -->

---

## 📖 Table of Contents

- [🚀 Features](#-features)
- [📦 Prerequisites](#-prerequisites)
- [🔧 Installation](#-installation)
- [🎯 How to Play](#-how-to-play)
- [🏗️ Code Structure](#️-code-structure)
- [🧠 Data Structures](#-data-structures)
- [📚 Libraries](#-libraries)
- [🧩 Functions](#-functions)
- [🔍 Code Deep Dive](#-code-deep-dive)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

## 🚀 Features

- 🌟 **Graphical Interface** with SDL2 animations
- 📂 **Multiple Word Categories** (Fruits, Jobs, Plants, etc.)
- 🎚️ **Difficulty Levels** (Easy/Hard)
- 💡 **Hint System** (2 hints per game)
- ⏳ **90-Second Timer**
- 📊 **Win/Loss Tracking**
- 🖼️ **Animated Win/Lose Screens**

---

## 📦 Prerequisites

- **C++ Compiler**: GCC, Clang, or MSVC
- **SDL2 Libraries**:
  - SDL2 (v2.0.14+)
  - SDL2_image (v2.0.5+)
  - SDL2_ttf (v2.0.15+)
- **Font File**: [VeraMoBd.ttf](https://www.fontsquirrel.com/fonts/vera-mono) (included)
- **Assets**: PNG images & word lists (included)

---

## 🔧 Installation

### 🪟 Windows (CodeBlocks)
1. Download [SDL2 Development Libraries](https://libsdl.org/download-2.0.php)
2. Open `hangman.cbp` in CodeBlocks
3. Configure include paths for SDL2 in project settings
4. Build & Run (F9)

### 🐧 Linux/macOS (Manual Build)
```bash
git clone https://github.com/yourusername/hangman.git
cd hangman
g++ -o hangman main.cpp Game.cpp SkickSDL.cpp painter.cpp utility.cpp \
-I/path/to/SDL2/include -L/path/to/SDL2/lib \
-lSDL2 -lSDL2_image -lSDL2_ttf
