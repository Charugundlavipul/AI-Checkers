# CheckBot Alpha

## Overview

Checkbot Alpha is a checkers game built using Python's `pygame` library. The project is structured with different classes such as `Board`, `Piece`, `Game`, and `Algorithms` to manage the game’s functionality and the bot's move strategies.

## GUI

We used the `pygame` library in Python to create the checkers GUI. Different classes such as `Board`, `Piece`, etc., were created for better readability and understanding.

The **BoardnPawns** file contains two classes: `Board` and `Piece`. These classes include methods that:
- Return the valid pieces and kill pieces in the current board position for a given color.
- Handle the movement of the pieces.
- Return the valid spaces for a given piece.
- Include general methods such as drawing the board, filling the initial pieces, drawing pieces on the window, and promoting a piece to a king.

The **Game** class handles the flow of the game by:
- Managing the selection of a piece and the destination to move that piece.
- Drawing and updating the window after every move.
- Checking for win or tie conditions.

Additionally, the **Algorithms** class contains the implementations for both the **Random** algorithm and the **Minimax** algorithm, which are used for the bot's moves.

## Strategies Used for the Bot

### Random
- A random piece is selected from the set of valid pieces for that move.
- From the selected piece, a random valid move is chosen.
- These selections are reflected on the board after the bot's next move.

### Minimax
- The evaluation score is calculated using the difference between bot’s and human’s pieces along with the difference between bot’s and human’s kings:

  **Score = (Bot - Human + BotKings - HumanKings)**
  
- The bot aims to maximize this score, while the human aims to minimize it.
- A search depth of three is used. If it is the human's move, the algorithm assumes the best move is played (lowest score); if it's the bot's move, the highest score is considered.
- The minimax function is traversed recursively:
  - The base case is reached when the depth is zero or when any player wins.
  - A Boolean variable indicates whether it is the bot's move and alternates with each recursive call.
  - For bot moves (`bot = true`), the maximum score is selected.
  - For human moves (`bot = false`), the minimum score is selected.
- The function ultimately returns the best move for the bot.

## Comparison of the Strategies

It is evident that the minimax algorithm is superior, as it makes calculated moves, whereas the random algorithm simply selects moves arbitrarily.

### Algorithm for Finding Valid Spaces for Pieces

- The algorithm first checks whether a piece is moving up or down (i.e., blue or red).
- Two functions, `checkLeft` and `checkRight`, are used to inspect diagonal directions:
  - They check for an empty space or a piece of a different color.
  - If a kill is possible, the destination (i.e., the valid move) is stored in a dictionary mapping to the pieces that can be captured or skipped.
- These functions are called recursively to cover all possible moves.

For king pieces, a modified algorithm is required since they can move both upward and downward:
- Two functions, `checkKingLeft` and `checkKingRight`, simultaneously check the left/right and top/bottom directions.
- These methods are also called recursively to cover all valid moves for kings.

## Screenshots

### Start Of Game
![Screenshot 2022-05-21 204758](https://user-images.githubusercontent.com/65329637/169658416-e992757c-3b9c-4573-953a-8f8f543be175.png)

### First Move Of Bot
![Screenshot 2022-05-21 204847](https://user-images.githubusercontent.com/65329637/169658431-85609561-d3d2-4ee0-ad93-af451e7859db.png)

### King Coin
![King Coin](https://user-images.githubusercontent.com/65329637/169658462-87d4f4b2-f08f-4ac2-9f5a-4f96a706e2b7.png)

### Bot Win
![Bot Win](https://user-images.githubusercontent.com/65329637/169658486-ae5c6936-29b0-4f87-ac2b-c6d605cee937.png)
