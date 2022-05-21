# AI-Checkers
## GUI:
We used pygame library from python to create the checkers GUI. Created Different classes like Board, Piece etc. for good readability and understanding. 
BoardnPawns file has two class board and piece which have different methods like it returns the validPieces, KillPieces in the present board position for the given color, it also handles the movement of the pieces, it returns the valid spaces for the given piece also few general methods like drawing the board and filling the initial pieces also methods like drawing the piece on our window, making the piece a king etc. Game class handles the flow of the game like selecting a piece and selecting the position into which the piece should be moved, it draws the window and updates it after every move, it checks for win or tie etc. 
Created the algorithms class which has the random algorithm and minimax algorithm which are used for AI move. 
## Strategies used for the AI:
### Random –
Selected a random piece from the set of valid pieces for that move. From the selected random piece, we selected a random that piece could make. 
These selections will be reflected in the board after AI’s next move.
### MiniMax – 
Used the sum of difference in AI’s and Human’s pieces and difference in AI’s and Human’s kings as the Evaluation Score. Score = (AI – Human + AIKings – HumanKings).
AI tries to maximize this score and human tries to minimize this score. We used a depth of three for our algorithm, if it is the human’s move, we assume he plays the best move and consider the lowest score and for the AI’s move we consider the max score as AI tries to maximize it (i.e., play the best move possible according to the evaluation). 
Traversed the minimax function using recursion, we started evaluating the boards when we reach the bottom of the tree (i.e., when the depth is zero) or when any player wins. We call the minimax function recursively, changing the Boolean variable AI to True and False Alternatively. 
In the first Iteration AI is true as it is AI’s move, in the next iteration we send the AI parameter as false. In such a case the different human’s moves are considered and it goes on like this. 
After the base case is satisfied, least score from every AI = false iteration and Highest score from every AI = true iteration is considered. Finally, this function returns the best move for the AI to play.
## Comparison of the above Strategies:
We can clearly see that minimax is the better algorithm as it makes its moves in a calculated manner whereas random algorithm just plays random moves. 
### Algorithm used for finding the valid spaces for the required Pieces:
We checked if the piece is moving up or down (i.e., blue or red). 
Then we have written two functions checkLeft and checkRight which which in the left and right directions respectively in a diagonal manner and check for an empty space, or a piece of a different color. 
If a kill can be made, we have stored the destination (i.e., the valid move) in the dictionary as the key which points to the pieces which can be killed or skipped. 
We call these functions recursively to cover all possible combinations. 
For the king piece the above algorithm doesn’t work as it checks for the valid move in either the top or the bottom direction. 
A king can up and down so he can make kills in two opposite directions.
We have written a similar algorithm, two methods called checkKingLeft and checKingRight which check left and right and also simultaneously check top and bottom. 
We have called these methods recursively to achieve this task. 
