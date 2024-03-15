/**
 * This program implements a simple command-line Tic-Tac-Toe game where two players take turns entering their moves until one of them wins or the game ends in a draw.
 * The game board is represented by a 3x3 grid of characters. Players input their moves by specifying the row and column where they want to place their symbol ('X' or 'O').
 * The program checks for winning combinations after each move to determine if a player has won the game.
 */
public class Main {
  
  /**
   * The main method initializes the Tic-Tac-Toe board, sets up a Scanner for user input, and starts a loop that continues until the game is over.
   * Inside the loop, the current state of the board is printed, and then the current player is prompted to enter their move.
   * The move is validated to ensure that it's within the bounds of the board and that the chosen cell is empty.
   * If the move is valid, it's placed on the board, and then the haveWon method is called to check if the current player has won the game.
   * If the current player has won, the game ends and the winner is announced. Otherwise, it switches to the next player.
   * If the move is invalid, an error message is displayed, and the current player is prompted to enter their move again.
   * After the game ends, the final state of the board is printed.
   * @param args Command-line arguments (not used)
   */
  public static void main(String[] args) {
    // Initialize the Tic-Tac-Toe board
    char[][] board = new char[3][3];
    for (int row = 0; row < board.length; row++) {
      for (int col = 0; col < board[row].length; col++) {
        board[row][col] = ' ';
      }
    }

    // Initialize variables for the current player and game state
    char player = 'X';
    boolean gameOver = false;
    Scanner scanner = new Scanner(System.in);

    // Main game loop
    while (!gameOver) {
      // Print the current state of the board
      printBoard(board);
      System.out.print("Player " + player + " enter: ");
      // Prompt the current player to enter their move
      int row = scanner.nextInt();
      int col = scanner.nextInt();
      System.out.println();

      // Validate the move and update the board
      if (board[row][col] == ' ') {
        board[row][col] = player; // place the element
        gameOver = haveWon(board, player);
        // Check if the current player has won
        if (gameOver) {
          System.out.println("Player " + player + " has won: ");
        } else {
          // Switch to the next player
          player = (player == 'X') ? 'O' : 'X';
        }
      } else {
        // Display an error message for invalid moves
        System.out.println("Invalid move. Try again!");
      }
    }
    // Print the final state of the board after the game ends
    printBoard(board);
  }

  /**
   * Checks whether the specified player has won the game by examining the rows, columns, and diagonals of the board.
   * @param board The current state of the Tic-Tac-Toe board
   * @param player The player ('X' or 'O') to check for winning combinations
   * @return True if the player has won the game, otherwise false
   */
  public static boolean haveWon(char[][] board, char player) {
    // Check the rows for winning combinations
    for (int row = 0; row < board.length; row++) {
      if (board[row][0] == player && board[row][1] == player && board[row][2] == player) {
        return true;
      }
    }

    // Check the columns for winning combinations
    for (int col = 0; col < board[0].length; col++) {
      if (board[0][col] == player && board[1][col] == player && board[2][col] == player) {
        return true;
      }
    }

    // Check the diagonals for winning combinations
    if (board[0][0] == player && board[1][1] == player && board[2][2] == player) {
      return true;
    }

    if (board[0][2] == player && board[1][1] == player && board[2][0] == player) {
      return true;
    }
    // No winning combinations found
    return false;
  }

  /**
   * Prints the current state of the Tic-Tac-Toe board.
   * @param board The current state of the Tic-Tac-Toe board
   */
  public static void printBoard(char[][] board) {
    for (int row = 0; row < board.length; row++) {
      for (int col = 0; col < board[row].length; col++) {
        System.out.print(board[row][col] + " | ");
      }
      System.out.println();
    }
  }
}
