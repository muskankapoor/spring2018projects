# Connect 4 Project Plan 
## Shariar Kabir, Jason Chen, Boubacar Diallo

Roles: dev1, dev2, dev3

Each assigned role is designated with an '@'

### Main Program Structure
  * ```main()```  **(Lobby Phase)**: handles interactions in between games  *@dev1*
    * Initiate a game at first, then continuosly check user input to determine if another game should be started
    * If user inputs a value that evalauates to true, call playGame() and play another game **(Game Start Phase)**
    * Once the user inputs a value that evaluates to false, end the program
  * ```void playGame()``` **(Play Phase)**: handles all in game actions    
    * Initialize empty board (7 x 7 2D vector) with placeholder characters that signify 'empty' spots  *@dev2*
    * Initialize ```int turn = 1```, a counter to keep track of which turn it is                       *@dev2*
    * Game Loop: while the game isn't over, use the game API functions to complete another turn, then increment ```turn```
    * Once ```isGameOver()``` returns true, call ```endGame(int winner)``` **(Game End Phase)** 


### Game API (functions used by ```playGame()``` in the play phase) 
  * ```int get_player(turn)```  *@dev2*
      * if turn % 2 == 1 &rarr; player 1; if even &rarr; player 2
  * ```int nextFreeSpace(int col)```  *@dev3* 
      * returns index of first place where a chip can be placed in ```col``` of the game board vector
      * if the column is full returns -1
  * ```void place_chip(int col)```   *@dev1*
      * takes an int to place the player’s chip
      * calls nextFreeSpace to see if it is placeable (the column isnt full), if not then show error message to prompt
         player to choose again. 
      * if it is placeable, replace the placeholder character with the char representing the color for the current player in the 2D vector at that column
  * ```void print_board()```  *@dev2* 
      * prints out the 2D vector onto the terminal after each turn is completed
  * ```bool isGameOver()```  *@dev3, dev2, dev1*
      * checks if game has finished after a player puts a chip. 
      * Checks each chip and goes max of 4 up, down, left, right, diagonal(s). 
      * ie - starts with one direction, and recursively loops in that direction till check_space returns true 4 times in a row. 
      * Has to call check_space() with the direction that is chosen (so would make a L or non-straight line) and the value of the row and col of the chip by the double for loop.
      * If those loops determine there is no connect 4, check if ```turn``` equals the number of board spaces (the board is completely full), then end with a draw.
  * ```bool check_space(int r, int c, string direction, char playercolor)```  *@dev2*
      * check if the space same “color” chip as the one before.
  * ```void endGame(int winner)``` *@dev3*
    * if winner == 1 &rarr; player 1 won, if winner == 2 &rarr; player 2 won, if winner == 0 &rarr; it was a draw
    * show "Game Ended" UI with the winning and losing player (or draw)
   
