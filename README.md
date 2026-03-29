# Artificial-and-Computational-Intelligence-Game-Playing
The game which is described is a two-player crossword puzzle where players take turns placing words on a grid. The goal is to correctly place words to maximize their points, which are awarded based on the character count of the word. If a player places a word incorrectly, they lose a point, and the other player has a chance to place it correctly.

Here's a step-by-step explanation of how the game works:

Setup:
o	There is a list of words available for the game.
o	The game is played on a 10x7 grid initially filled with empty spaces.
o	Each player starts with a score of 0.
Gameplay:
o	The game consists of 10 rounds.
o	In each round, players take turns. Player 1 starts the first round.
o	For each turn, a player selects a word from the available words and chooses a grid location to place the word. The format for grid locations is row and column, such as "5D" or "6A".
o	If the chosen grid location is already occupied by a word, the player loses a point, and their turn is not counted. They must choose another location.
o	If the chosen grid location is valid and the placed word matches the chosen word, the player's score increases by the length of the word.
o	If the chosen grid location is valid but the placed word doesn't match the chosen word, the player loses a point.
Scoring:
o	Players receive points based on the character count of the correctly placed word. For example, if "cat" is placed correctly, the player gets 3 points.
End of Round and Game:
o	After each round, the scores of both players are displayed.
o	The game continues for 10 rounds, with players taking turns and placing words.
o	At the end of the 10 rounds, the two players with the highest scores are identified as the best solutions.
Best Solutions:
o	The game concludes by identifying the two players with the highest scores after 10 rounds.
o	These two players are considered the best solutions.
Rules of Game-Play: 
At each step, user would be given possible and available words. 
o	Step1 : User1 (maximizer player) will give dynamic inputs : word , x , y , direction_to_place_word. 
1.	If correct sequence of words given, score would be added by number of characters in word.
2.	If wrong move selected, then score will be reduced by -1
                    For example : prompt looks like : sample from a run :
 

o	Step2 : Program Agent (minimizer player) will select best possible move from among the remaining word from words list. Best move would be decided based on :
1.	Placing the available words.
2.	Calculating score with this move
3.	Recursively giving turn to other player and so on. 
4.	Finally, based on score : best move decided which includes “word”, x, y, direction. 
	P1 selected PEACOCK at 5,0 to be set across(horizontal)
	In return, P2 expanded game-tree and selected SPARROW at 3,2 with vertical direction
 
o	Step3 : Game continues till:
1.	Either all words from word list exhausted. 
2.	Words remain, but no possible move. 
 
o	Step4 : Result declaration:
1.	At each iteration, players scores are displayed. 
2.	At end of game, result declared based on final scores of each player. 
 
Sample Result from one of the iteration shown below : Player1 won with score as 21. 
	 

2.	Python Implementation Code Flow

o	The code has provided is a Python implementation of the two-player solution-based crossword puzzle game you described earlier. Let me walk you through the code step by step:


Word List and Initialization:
o	A list of words (word_list) is provided for the crossword puzzle.
o	A 10x7 crossword grid (grid) is initialized with empty spaces.
o	Player scores (player_scores) are initialized with zeros.

Game Loop (10 Rounds): The game is played for 10 rounds using a for loop. In each round:
o	The word list for the current round is shuffled using random.shuffle.
o	Each player (0 and 1) takes turns placing words on the grid.

Word Placement Logic:
o	The current grid is displayed to both players using nested for loops.
o	Players are prompted to input the row and column for placing the word.

Validation and Scoring:
o	The code checks if the word placement is valid:
	If the word would exceed the grid boundaries or overlap with an existing word, the player loses a point and is notified about the incorrect placement.
	Otherwise, the word is placed on the grid, and the player's score is updated based on the length of the word.
Score Display:
o	After each round, the scores for both players are displayed.

Selecting Best Solutions:
o	After 10 rounds, the code selects the two players with the highest scores as the best solutions.
o	The enumerate function is used to associate each player's score with their index (0 or 1).
o	The sorted function sorts these associations based on scores in descending order.
o	The two players with the highest scores are extracted using slicing.
Final Output: The code concludes by printing the best solutions with their corresponding scores.



3.	Python Implementation Code Output (One of the sample output taken)
‘#’  Blocked location. Not possible to place any character. 
‘_’  Allowed location to place a character. 

Iteration 1 : To demonstrate word placing : 
Score of Player1 ==  0 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU', 'SPARROW']
Player 1, enter your move (word x y direction): PEACOCK 5 0 across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
P E A C O C K
# # _ # # # #
_ _ _ _ _ _ #
# # _ # # # #
# # _ _ _ _ #

Score of Player1 ==  7 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU', 'SPARROW']
Player 2 chooses SPARROW at (3, 2) down
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S _ _ _ _
# # P # # # #
P E A C O C K
# # R # # # #
_ _ R _ _ _ #
# # O # # # #
# # W _ _ _ #

Score of Player1 ==  7 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU']
Player 1, enter your move (word x y direction): PARROT 7 0 across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S _ _ _ _
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W _ _ _ #

Score of Player1 ==  13 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'SWANE', 'WREN', 'CROW', 'EMU']
Player 2 chooses EMU at (9, 3) across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S _ _ _ _
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  13 Score of Player2 ==  10
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'SWANE', 'WREN', 'CROW']
Player 1, enter your move (word x y direction): SWANE 3 2 across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  18 Score of Player2 ==  10
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'WREN', 'CROW']
Player 2 chooses CROW at (0, 3) down
Current board:
# _ _ C _ # _
_ # # R # # _
_ # # O # # _
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  18 Score of Player2 ==  14
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'WREN']
Player 1, enter your move (word x y direction): DUCK 0 1 across
Current board:
# D U C K # _
_ # # R # # _
_ # # O # # _
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  22 Score of Player2 ==  14
WORD LIST TO CHOOSE FROM ['DOVE', 'WREN']
Player 2 chooses DOVE at (0, 6) down
Current board:
# D U C K # D
_ # # R # # O
_ # # O # # V
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  22 Score of Player2 ==  18
WORD LIST TO CHOOSE FROM ['WREN']
Player 1, enter your move (word x y direction): WREN 1 0 down
Invalid move! One point deducted.
Score of Player1 ==  21 Score of Player2 ==  18
WORD LIST TO CHOOSE FROM []

GAME OVER : NO MORE POSSIBLE MOVES NOW

GAME SCORE : Player1-score(User) ==  21 Player2-score(AI agent) ==  18
WINNER IS Player1




Iteration 2 : 


Score of Player1 ==  0 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU', 'SPARROW']
Player 1, enter your move (word x y direction): DUCK 0 1 across
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
_ _ _ _ _ _ _
# # _ # # # #
_ _ _ _ _ _ #
# # _ # # # #
# # _ _ _ _ #

Score of Player1 ==  4 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU', 'SPARROW']
Player 2 chooses SPARROW at (5, 0) across
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
S P A R R O W
# # _ # # # #
_ _ _ _ _ _ #
# # _ # # # #
# # _ _ _ _ #

Score of Player1 ==  4 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU']
Player 1, enter your move (word x y direction): PEACOCK 7 0 across
Invalid move! One point deducted.
Score of Player1 ==  3 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DOVE', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU']
Player 2 chooses EMU at (9, 3) across
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
S P A R R O W
# # _ # # # #
_ _ _ _ _ _ #
# # _ # # # #
# # _ E M U #

Score of Player1 ==  3 Score of Player2 ==  10
WORD LIST TO CHOOSE FROM ['DOVE', 'PARROT', 'SWANE', 'WREN', 'CROW']
Player 1, enter your move (word x y direction): PARROT 7 0 across
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
S P A R R O W
# # _ # # # #
P A R R O T #
# # _ # # # #
# # _ E M U #

Score of Player1 ==  9 Score of Player2 ==  10
WORD LIST TO CHOOSE FROM ['DOVE', 'SWANE', 'WREN', 'CROW']
Player 2 chooses CROW at (6, 2) down
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # _ _ _ _ _
# # _ # # # #
S P A R R O W
# # C # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  9 Score of Player2 ==  14
WORD LIST TO CHOOSE FROM ['DOVE', 'SWANE', 'WREN']
Player 1, enter your move (word x y direction): SWANE 3 2 across
Current board:
# D U C K # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # _ # # # #
S P A R R O W
# # C # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  14 Score of Player2 ==  14
WORD LIST TO CHOOSE FROM ['DOVE', 'WREN']
Player 2 chooses DOVE at (0, 6) down
Current board:
# D U C K # D
_ # # _ # # O
_ # # _ # # V
_ # S W A N E
# # _ # # # #
S P A R R O W
# # C # # # #
P A R R O T #
# # O # # # #
# # W E M U #

Score of Player1 ==  14 Score of Player2 ==  18
WORD LIST TO CHOOSE FROM ['WREN']
Player 1, enter your move (word x y direction): WREN 1 0 down
Invalid move! One point deducted.
Score of Player1 ==  13 Score of Player2 ==  18
WORD LIST TO CHOOSE FROM []

GAME OVER : NO MORE POSSIBLE MOVES NOW

GAME SCORE : Player1-score(User) ==  13 Player2-score(AI agent) ==  18
WINNER IS Player2



Iteration 3 : Shows Player1 winning choosing intelligently longer words at correct places
Score of Player1 ==  0 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU', 'SPARROW']
Player 1, enter your move (word x y direction): SPARROW 3 2 down
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S _ _ _ _
# # P # # # #
_ _ A _ _ _ _
# # R # # # #
_ _ R _ _ _ #
# # O # # # #
# # W _ _ _ #

Score of Player1 ==  7 Score of Player2 ==  0
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW', 'EMU']
Player 2 chooses EMU at (9, 3) across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S _ _ _ _
# # P # # # #
_ _ A _ _ _ _
# # R # # # #
_ _ R _ _ _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  7 Score of Player2 ==  3
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'SWANE', 'WREN', 'CROW']
Player 1, enter your move (word x y direction): SWANE 3 2 across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # P # # # #
_ _ A _ _ _ _
# # R # # # #
_ _ R _ _ _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  12 Score of Player2 ==  3
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'WREN', 'CROW']
Player 2 chooses CROW at (7, 1) across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # P # # # #
_ _ A _ _ _ _
# # R # # # #
_ C R O W _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  12 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PEACOCK', 'PARROT', 'WREN']
Player 1, enter your move (word x y direction): PEACOCK 5 0 across
Current board:
# _ _ _ _ # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
_ C R O W _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  19 Score of Player2 ==  7
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PARROT', 'WREN']
Player 2 chooses WREN at (0, 1) across
Current board:
# W R E N # _
_ # # _ # # _
_ # # _ # # _
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
_ C R O W _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  19 Score of Player2 ==  11
WORD LIST TO CHOOSE FROM ['DUCK', 'DOVE', 'PARROT']
Player 1, enter your move (word x y direction): DOVE 0 6 down
Current board:
# W R E N # D
_ # # _ # # O
_ # # _ # # V
_ # S W A N E
# # P # # # #
P E A C O C K
# # R # # # #
_ C R O W _ #
# # O # # # #
# # W E M U #

Score of Player1 ==  23 Score of Player2 ==  11
WORD LIST TO CHOOSE FROM ['DUCK', 'PARROT']

GAME OVER : NO MORE POSSIBLE MOVES NOW

GAME SCORE : Player1-score(User) ==  23 Player2-score(AI agent) ==  11
WINNER IS Player1


