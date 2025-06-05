This is a console-based shooter game called "Taha's Console Shooter," inspired by classic arcade games like Space Invaders. The player controls a character ('P') at the bottom of a 40x20 grid, moving left or right and shooting bullets ('|') to destroy enemies ('E') that move horizontally and shoot back ('.'). The game features multiple waves of enemies, a scoring system, health tracking, and levels. The game ends if the player's health reaches zero, enemies reach the bottom, or the player achieves a score of 100 (win condition). The display uses double buffering for smooth rendering, and the game includes a heads-up display (HUD) showing health, score, level, and wave.

Header Files and Their Functions
<iostream>: Provides input/output operations (e.g., cout for printing to the console).
<vector>: Enables the use of dynamic arrays (vector) to store enemies and bullets.
<conio.h>: Provides console input functions like _kbhit() (checks for keypress) and _getch() (reads a keypress without echoing).
<windows.h>: Provides Windows-specific functions for console manipulation, such as GetStdHandle, WriteConsoleOutput, SetConsoleTitleA, and SetConsoleScreenBufferSize.
<cstdlib>: Includes functions like rand() for random number generation and srand() for seeding the random number generator.
<ctime>: Provides time() to get the current time for seeding random numbers.
<iomanip>: Not directly used in the code (likely included for formatting but unused).
<algorithm>: Provides max() to ensure enemy speed and shooting delay don't go below minimum values.
C++ Functions Used
Standard Library Functions:
cout (<iostream>): Prints the exit prompt.
to_string (<string>): Converts numbers to strings for HUD display.
rand, srand (<cstdlib>): Generate random numbers for enemy shooting.
time (<ctime>): Gets current time for random seed.
max (<algorithm>): Ensures minimum values for enemySpeed and enemyShootDelay.
Console Input Functions (<conio.h>):
_kbhit(): Checks if a key is pressed.
_getch(): Reads a keypress without displaying it.
Windows API Functions (<windows.h>):
GetStdHandle: Gets the console output handle.
WriteConsoleOutput: Writes the buffer to the console.
SetConsoleTitleA: Sets the console window title.
SetConsoleScreenBufferSize: Sets the console buffer size.
Sleep: Pauses execution for a specified time (50ms per frame).
Vector Operations (<vector>):
push_back: Adds elements to vectors (enemies, bullets).
erase: Removes elements from vectors (enemies, bullets).
size: Gets the number of elements in a vector.
empty: Checks if a vector is empty.
begin: Used with erase to remove elements at specific indices.
Custom Functions
ClearBuffer: Clears the console buffer by setting all characters to spaces and default color.
WriteToBuffer: Writes a character to a specific position in the buffer with a given color.
Setup: Initializes the game by allocating the buffer and spawning the first wave of enemies.
DrawTitle: Displays the game title at the top of the screen.
DrawGameOver: Shows "GAME OVER" when the player loses.
DrawWin: Shows "YOU WIN!" when the player wins.
DrawHUD: Displays health, score, level, and wave information.
DrawBoundary: Draws the game boundaries (top and bottom).
DrawGameField: Renders the game field, including player, enemies, and bullets.
DrawInstructions: Shows control instructions or final score when the game ends.
Draw: Clears the buffer, draws all elements, and updates the console.
Input: Handles player input (move left/right, shoot, quit).
SpawnNewWave: Spawns a new wave of enemies, increases wave number, and adjusts difficulty.
Logic: Updates game state (moves bullets/enemies, checks collisions, updates health/score).
Explanation of the Code in Simple Words
This game is a simple, text-based shooting game played in the console. Here's how it works in plain language:

Setup:
The game creates a 40x20 playing field with boundaries ('#') and a player ('P') at the bottom.
Enemies ('E') are placed in a grid at the top.
A "buffer" (like an invisible canvas) is used to draw everything smoothly without flickering.
Gameplay Loop (runs every 50ms):
Drawing: The screen is cleared, and the game draws the title, player, enemies, bullets, and HUD (health, score, level, wave). Colors make it visually appealing (player is blue, enemies are magenta, etc.).
Input: The player uses 'A' to move left, 'D' to move right, 'SPACE' to shoot, or 'Q' to quit. The game checks for keypresses without pausing.
Logic:
Enemies move side to side and down when they hit the walls.
Enemies randomly shoot bullets ('.') downward.
Player bullets ('|') move up, and enemy bullets move down.
If a player bullet hits an enemy, the enemy is removed, and the score increases by 10.
If an enemy bullet hits the player, health decreases. If health reaches 0, the game ends.
If enemies reach the bottom, the game ends.
If the score reaches 100, the player wins.
When all enemies are defeated, a new wave spawns, with faster enemies and more frequent shooting.
Endgame:
On game over, the final score and enemies killed are shown.
If the player wins (score ≥ 100), a "YOU WIN!" message appears.
The player presses a key to exit.
Technical Details:
The game uses a double-buffering technique to draw everything off-screen first, then display it all at once for smooth visuals.
Random numbers decide when enemies shoot.
The console window is customized with a title and specific size
