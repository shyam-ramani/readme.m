Hangman Game: Core Functional Architecture
Table of Contents
Main Game Loop

Game Class Breakdown

Animation System

Suggestion System

Key Strengths

Technical Highlights

Performance Considerations

Unique Features

1. Main Game Loop
Location: main.cpp

cpp
Copy
Edit
while (hangman->playing) {
    hangman->startGame();
    do {
        hangman->renderGameSDL();
        hangman->guessEvent();
        hangman->handleGuess();
        hangman->updateTime();
    } while (hangman->guessing());
    hangman->gameOver();
}
Key Flow:
Initialize game session

Continuous rendering/input loop

Real-time time management

State transition handling

2. Game Class Breakdown
a. startGame()
cpp
Copy
Edit
void Game::startGame() {
    chooseCategory();
    chooseDifficulty();
    initWord();
    guessedWord = string(word.length(), '-');
    // ... other initializations ...
    time(&startTime);
}
Responsibilities:

Game reset

UI for category/difficulty selection

Word initialization from file

Timer and state initialization

b. handleGuess()
cpp
Copy
Edit
void Game::handleGuess() {
    if (guessChar == '$') getSuggest();
    else if (contains(word, guessChar)) {
        updateGuessedWord();
        updateSuggest();
    } else {
        badGuessed();
        renderPlane(guessChar, 0);
    }
}
Logic Flow:

Hint (via spacebar)

Correct guess update

Incorrect guess and animation

c. updateGuessedWord()
cpp
Copy
Edit
void Game::updateGuessedWord() {
    for (int i = 0; i < n; i++) {
        if (word[i] == guessChar) {
            guessedWord[i] = guessChar;
            numOfChar++;
        }
    }
    renderPlane(guessChar, numOfChar);
}
Core Algorithm:

Linear scan through word

Update guessed buffer

Show plane animation with letter

3. Animation System
renderPlane()
cpp
Copy
Edit
void Game::renderPlane(char guessedChar, int num) {
    int i = -300;
    while (i < 1000 && !skip) {
        SDL->createImage("plane.png", i, 0);
        SDL->createTextTexture(...);
        i += 5; // Animation speed
    }
}
Parameters:

guessedChar: Current guess

num: Occurrence count

Mechanics:

Right-to-left sprite motion

Frame-independent timing

Spacebar interruption

4. Suggestion System
updateSuggest()
cpp
Copy
Edit
void Game::updateSuggest() {
    unordered_map<char, int> m;
    for (char c : word) 
        if (guessedWord.find(c) == -1)
            m[c]++;
    maxSuggest = m.size() / 2;
}
Algorithm:

Count unguessed unique letters

Hints limited to 50% of them

Purpose:

Prevent hint abuse

Add dynamic difficulty

5. Key Strengths
1. Visual Feedback System
Assets:

hang0.png to hang7.png: Hangman states

free0-3.png / hanged0-3.png: End-game animations

plane.png: Plane sprite animation

2. Time Management
cpp
Copy
Edit
void Game::updateTime() {
    time_t now;
    time(&now);
    timeLeft = playTime - difftime(now, startTime) + animatedTime;
}
Features:

Real-time countdown

Animation time compensation

3. Input Handling
cpp
Copy
Edit
void Game::guessEvent() {
    string keyName = SDL_GetKeyName(...);
    if (keyName == "Space") guessChar = '$';
    else if (keyName[0] >= 'A' && keyName[0] <= 'Z')
        guessChar = keyName[0];
}
Features:

Normalizes input to uppercase

Special key handling

Hint via spacebar

6. Technical Highlights
1. Resource Management
cpp
Copy
Edit
void SkickSDL::createImage(string fileName, int x, int y) {
    SDL_Texture* texture = painter->loadImage(...);
    // ... render ...
    SDL_DestroyTexture(texture); // Cleanup
}
Practices:

Centralized image loader

Texture cleanup after use

Avoid memory leaks

2. State Management
cpp
Copy
Edit
class Game {
    bool playing; // Session active
    bool quit;    // Program exit
    int win;      // Persistent stats
    int loss;
}
Design:

Flag-based state control

Persistent session tracking

7. Performance Considerations
1. Rendering Optimizations
VSync: Enabled for smooth rendering

Texture Caching: Reuses frequent assets

Resolution: Fixed logical 950x900 across devices

2. Memory Management
cpp
Copy
Edit
SkickSDL::~SkickSDL() {
    SDL_DestroyRenderer(...);
    // ... full cleanup ...
}
Smart Handling:

RAII for SDL objects

Single font/surface instance

Immediate deallocation

8. Unique Features
1. Dynamic Difficulty
cpp
Copy
Edit
string chooseWord(...) {
    return (word.length() > 5 && difficult) 
        ? word : chooseWord(...);
}
Logic:

Recursively reselects based on length

Filters short/long words by mode

2. Progressive Hint Limiting
cpp
Copy
Edit
void Game::updateSuggest() {
    maxSuggest = m.size() / 2;
}
Effect:

Limits hints to half of remaining letters

Balances challenge as word nears completion
