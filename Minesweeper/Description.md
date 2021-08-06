# Minesweeper
***The aim of minesweeper is to reveal every square in the minefield except for the ones containing mines.***

Minesweeper is already capable of drawing a certain view of the minefield, but it will be up to you to write code so that it can get input from the user on where mines are initially placed, and read commands to make the correct changes to the minefield. The finished product of Minesweeper is a simplified playable version of the game.

The Minefield

The minefield is a two dimensional array (an array of arrays) of integers that represents the space that the game is played in. We will be referring to individual elements of these arrays as squares in the minefield.

The minefield is a fixed size grid and has SIZE rows, and SIZE columns. SIZE is a #define'd constant.

Both the rows and columns start at 0, not at 1.

The top left corner of the grid is (0, 0) and the bottom right corner of the grid is (SIZE - 1, SIZE - 1). Note that we are using rows as the first coordinate in pairs of coordinates.

For example, if we are given an input pair of coordinates 5 6, we will use that to find a particular square in our minefield by accessing the individual element in the array: minefield[5][6]



In the game of minesweeper these states are displayed to the player:

A revealed square
A square that is unrevealed
Since a square that has not been revealed may or may not contain a mine, there are actually 3 values a square can take. These are represented by the following #define'd integers:

#define VISIBLE_SAFE 0: this represents a square that has been revealed.
#define HIDDEN_SAFE 1: this represents a square that has not been revealed but does not contain a mine.
#define HIDDEN_MINE 2: this represents a square that has not been revealed and contains a mine.
When the program is started, all of the squares should be HIDDEN_SAFE. The minefield is then populated with mines (i.e., HIDDEN_MINE) by scanning the locations of the mines, using the code you will write.

The way you reveal squares in the original minesweeper has been replaced by another revealing command:

REVEAL_CROSS: reveal the selected square, for each of the four directly connected squares, only reveal if they have no mines adjacent. This could result in your program revealing anything from 1 - 5 squares.


Please note: Connected refers to the 4 squares directly above, below, to the left, and to the rights of a square. While adjacent refers to the 8 surrounding squares of a grid square. For example, in the diagram below, there are 8 adjacent squares (in grey) to the square in yellow.



Your minesweeper program will have a way of checking how many mines are in a set of squares in a row, or in a square section of the minefield, and use these to give the user hints about the location of mines.

The game ends when either:

The game is won: All of the squares are revealed except for those containing mines.
The game is lost: A user attempts to reveal a square containing a mine.
Allowed C Features

There are no restrictions on C Features.

The only C features you will need are:

int variables;
if statements, including all relational and logical operators;
while loops;
int arrays, including two dimensional arrays;
printf and scanf; and
functions.
# Input Commands
The program should first ask for the number of mines as an integer. Then, the program will scan the locations of the mines as pairs of integers in the format: row column

After specifying the location of the mines, each command given to the program will be a series of integers. These input commands should continue to be read and executed until the game is won, lost, or when there is an EOF (Ctrl + D)

The first input will always be an integer representing the type of command, e.g. 1 means How many mines in a row?

Depending on what command the first integer specifies, you will then scan in some number of "arguments" (additional integers) that have a specific meaning for that command.

For example, 1 5 2 5 asks for how many mines in row 5 , from column 2 to 6 inclusive, checking along 5 columns in total.

Input to your program will be via standard input (e.g. typing into the terminal).

You can assume that the input will always be integers and that you will always receive the correct number of arguments for a command.

Details on each command that your program must implement are shown below

## Stage-1
### Placing Mines
As is, the program currently initializes the minefield to HIDDEN_SAFE then prints the minefield as a grid of integers.

The program should run as follows:

When the program first starts, it should prompt the user: How many mines?
The program should then scan in an integer entered by the user representing the number of mine locations that the user will give as coordinate pairs.
The program will then prompt the user to enter a list of coordinate pairs to specify the location of the mines. The coordinate pairs are entered as two integers, separated by a space, representing the row and column where a mine is located. These locations on the grid should then be changed to contain a mine (or rather the #define HIDDEN_MINE).
For example, when prompted with: Welcome to minesweeper! How many mines? The user may enter: 2 The program will expect 2 coordinate pairs to be entered (these may or may not be valid) and prompt the user to enter these values: Enter pairs: The user should then enter: 1 1, and then on the next line enter 5 7 which means place a mine at the square located at row 1, column 1, and another at row 5, column 7.

The program should then print Game started and print the minefield using the print_debug_minefield function provided in the starter code.

#### Invalid Inputs and Clarifications
You can assume the first number scanned in (i.e. the number of coordinate pairs specified) will always be valid (i.e. number of mines \> 0).
If the coordinate pair specified is out of bounds of the minefield, the program should not attempt to place it on the minefield.
##### Examples
./minesweeper

Welcome to minesweeper!

How many mines? 3

Enter pairs:

0 0

1 1

9 9

Game Started

2 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

## Counting Mines In A Row
For the second part of Stage 1, you will be implementing the first command: Detect Row.

After mines are placed, commands should be read in a loop until one of three events: the game is won, lost or there is an EOF (Ctrl + D)

The Detect Row command is specified by the integer 1, followed by a row number, column number, and a positive number of squares to check: 1 row column length (e.g. 1 4 5 2, to check the 2 squares from row 4, columns 5 to 6).

The output should be printed by your program as a message in the format: There are n mine(s) in row r, from column c to e Where n is the number of mines, r is the row number, c is the column number, and e is the end column.

Note that after each command has been scanned in and processed the minefield is printed once again.

### Invalid Inputs and Assumptions
Assume that the length is always a positive integer, you won't have to check for this
You should check for whether the coordinates are all within the minefield. If the start or end coordinates are outside the minefield, your program should print out Coordinates not on map.
Examples
./minesweeper

Welcome to minesweeper!

How many mines? 4

Enter pairs:

0 0

1 1

4 3

1 4

Game Started

2 1 1 1 1 1 1 1

1 2 1 1 2 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 2 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 0 5

There are 2 mine(s) in row 1, from column 0 to 4

2 1 1 1 1 1 1 1

1 2 1 1 2 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 2 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 3 5 4

Coordinates not on map

2 1 1 1 1 1 1 1

1 2 1 1 2 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 2 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

## Core – Stage 2
Why does this stage exist? This stage tests you on traversing a two dimensional array, and creating more complex while loop structures, it will also give you the opportunity to start working with functions if you choose to. This is slightly more complicated than the skills in Stage 1, and should help to cement your understanding and hope it will help you be more confident using these as tools in the future.

In Stage 2, you will implement a command to count the number of mines in a square section of the grid, as well as a command to reveal a cross on the grid (which makes it possible to win or lose the game).

We strongly recommend that you finish Stage 1 before attempting Stage 2, as it would be very hard to test whether Stage 2 is working without Stage 1.

Count The Number Of Mines In A Square
For the first part of Stage 2, you will be counting the number of mines in an n×n section of the grid using the Detect Square command.

The Detect Square command is specified by the number 2 followed by the row and column of the center of the square and an odd number representing the side length: 2 row column size

Your program should count the number of mines in this section and print it out in the format: There are n mines in the square centered at row r, column c, of size s, where n is the number of mines, r is the row number, c is the column number, and s is the size of the square.

Examples
1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 2 1 1 1 1

1 1 1 1 2 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

2 3 3 3

There are 2 mine(s) in the square centered at row 3, column 3 of size 3

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 2 1 1 1 1

1 1 1 1 2 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

This finds the number of mines in the following section:

#### Invalid Inputs and Assumptions
Assume that the size is always an odd, positive integer, you won't have to account for other sizes
You should check for whether the center coordinate is inside the minefield, if it isn't, your program should print out Coordinates not on map
You may be given squares that partly fall outside the minefield, these commands are valid as long as the centre is on the minefield, all locations inside the square and valid on the minefield should be checked
Reveal Cross
In order to complete the game, the user must be able to reveal the squares in the grid. For this we will create the command Reveal Cross. This command is used to reveal a section of the grid under certain rules. The reveal cross command is specified by the number 3 followed by the row and column of the center of the cross: 3 row column

#### Reveal cross follows these rules:

If the selected square contains a mine then the game is lost and the program should print out "Game over" and end the game. Note that the minefield should still be printed after processing the command which ends the game.
Each of the four squares connected to the selected square should only be revealed if it isn't a hidden mine, and there are no hidden mines adjacent to it.
If the selected square is on the edge of the minefield, only reveal squares which are valid squares inside the minefield.
If at the end of revealing the squares, all of the squares except the squares containing mines have been revealed, print "Game Won!" and end the game.
Take for example, the two scenarios below. In one, the square selected to be revealed (displayed in yellow) is connected to a mine, so only that square, and the connected squares with no hidden mines adjacent (any of the 8 squares surrounding it), are revealed. In the other scenario, there are no mines adjacent to the connected mine, so all five squares in the cross are revealed.

#### Invalid Input and Assumptions
You should check for whether the center coordinates given for Reveal Cross are within the minefield. If the center coordinates are outside the minefield, your program should print out Coordinates not on map.
Hints
Can you create a function for the first part of this stage and use it to help you with the second part of this stage?
Examples
./minesweeper

Welcome to minesweeper!

How many mines? 1

Enter pairs:

4 2

Game Started

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 2 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

3 3 4

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 0 1 1 1

1 1 1 1 0 0 1 1

1 1 2 1 0 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

./minesweeper

Welcome to minesweeper!

How many mines? 2

Enter pairs:

2 4

3 7

Game Started

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 2 1 1 1

1 1 1 1 1 1 1 2

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

3 2 5

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 2 0 1 1

1 1 1 1 1 1 1 2

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

## Core – Stage 3
Why does this stage exist? This stage makes the work you've done so far playable as a game, and tests you on being able to add extra functionality to your pre-existing code, and decision-making based on the contents of two dimensional arrays.

#### Restrict Hints
The commands Detect Row , and Detect Square are hints. In order to increase the difficulty of the game, the user should be restricted to only being able to use 3 hints. This can be any combination of Detect Row , and Detect Square.

Once the user has used their 3 hints, if they try to use another hint, they should see the message: Help already used

#### Invalid Input and Assumptions
You can assume that only valid commands requesting hints will be counted as used hints.
##### Examples
./minesweeper

Welcome to minesweeper!

How many mines? 1

Enter pairs:

1 1

Game Started

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 0 8

There are 1 mine(s) in row 1, from column 0 to 7

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 2 1 4

There are 0 mine(s) in row 2, from column 1 to 4

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

2 3 3 3

There are 0 mine(s) in the square centered at row 3, column 3 of size 3

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

2 2 3 3

Help already used

1 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

## Formatted Printing
The code to print out the minefield exactly as it is in the array is helpful in debugging, but it makes playing the game boring because you can see where the mines are.

We can introduce the game mode commands to switch between printing the default debug mode output, and gameplay mode , printing a stylised minefield.

Debug mode is the default mode when the program is run, however, it can be switched between gameplay mode and debug mode using the integer 4.

The format of the printed minefield is as follows:

Non-revealed squares are represented by two hashes.
Revealed squares contain either nothing (if there are no adjacent mines) or the number of adjacent mines if it is greater than zero.
A smiley face is shown as the game is being played, or when the game is won.
A dead frowning face is shown when the game is lost.
When gameplay mode is activated, your program program should display the message: Gameplay mode activated and then print out the formatted minefield. For example:

./minesweeper

Welcome to minesweeper!

How many mines? 3

Enter pairs:

0 0

1 1

2 1

Game Started

2 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

3 2 2

2 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 2 0 0 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

3 3 2

2 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 2 0 0 1 1 1 1

1 1 0 0 1 1 1 1

1 1 0 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

4

Gameplay mode activated

..

\/

00 01 02 03 04 05 06 07

00	## ## ## ## ## ## ## ##
01	## ## ## ## ## ## ## ##
02	## ## 02 ## ## ## ##
03	## ## 01 ## ## ## ##
04	## ## ## ## ## ## ##
05	## ## ## ## ## ## ## ##
06	## ## ## ## ## ## ## ##
07	## ## ## ## ## ## ## ##
Similarly, when the program is in gameplay mode and debug mode is activated, the program should print the message Debug mode activated and print out the minefield in the debugging format.

4

Debug mode activated

2 1 1 1 1 1 1 1

1 2 1 1 1 1 1 1

1 2 0 0 1 1 1 1

1 1 0 0 1 1 1 1

1 1 0 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

1 1 1 1 1 1 1 1

When the game ends and the player has lost, it should reveal the locations of the mines with a pair of brackets (i.e. ()). For example:

3 0 0

Game over

xx

/\

- 00 01 02 03 04 05 06 07

- 00	() ## ## ## ## ## ## ##
- 01	## () ## ## ## ## ## ##
- 02	## () 02 ## ## ## ##
- 03	## ## 01 ## ## ## ##
- 04	## ## ## ## ## ## ##
- 05	## ## ## ## ## ## ## ##
- 06	## ## ## ## ## ## ## ##
07	## ## ## ## ## ## ## ##
