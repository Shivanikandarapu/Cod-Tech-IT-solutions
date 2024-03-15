/**
 * Number Guessing Game
 * This program implements a simple number guessing game where the player has to guess a randomly generated number within a specified range and within a limited number of attempts.
 * The game consists of three rounds, and in each round, the player has ten attempts to guess the number.
 * The program provides feedback to the player after each guess, indicating whether the guess is too high, too low, or correct.
 * The player earns a score based on the number of attempts taken to guess the number successfully.
 * The total score is calculated by summing up the scores earned in each round.
 */

import java.util.Random;
import java.util.Scanner;

public class Task2 {
    private static final int MIN_RANGE = 1;
    private static final int MAX_RANGE = 100;
    private static final int MAX_ATTEMPTS = 10;
    private static final int MAX_ROUNDS = 3;

    /**
     * The main method serves as the entry point for the Number Guessing Game.
     * It initializes the game parameters such as range, number of attempts per round, and number of rounds.
     * It then runs the game loop for the specified number of rounds.
     * After each round, it calculates the score earned by the player and updates the total score.
     * Finally, it displays the total score once the game is over.
     * @param args Command-line arguments (not used)
     */
    public static void main(String[] args) {
        Random random = new Random();
        Scanner scanner = new Scanner(System.in);
        int totalScore = 0;

        // Display game information
        System.out.println("NUMBER GUESSING GAME");
        System.out.println("Total Number Of Rounds : 3");
        System.out.println("Attempts To Guess Number In Each Round : 10\n");

        // Loop through each round of the game
        for (int i = 1; i <= MAX_ROUNDS; i++) {
            int number = random.nextInt(MAX_RANGE) + MIN_RANGE;
            int attempts = 0;

            // Display round information
            System.out.printf("Round %d: Guess the number between %d and %d in %d attempts.\n", i, MIN_RANGE, MAX_RANGE,
                    MAX_ATTEMPTS);

            // Loop for each attempt in the current round
            while (attempts < MAX_ATTEMPTS) {
                System.out.println("Enter your guess : ");
                int guess_number = scanner.nextInt();
                attempts++;

                // Check if the guess is correct
                if (guess_number == number) {
                    int score = MAX_ATTEMPTS - attempts;
                    totalScore += score;
                    System.out.printf("Hurray! Number Guessed Successfully. Attempts = %d. Round Score = %d\n",
                            attempts, score);
                    break;
                } else if (guess_number < number) {
                    System.out.printf("The number is greater than %d. Attempts Left = %d.\n", guess_number,
                            MAX_ATTEMPTS - attempts);
                } else if (guess_number > number) {
                    System.out.printf("The number is less than %d. Attempts Left = %d.\n", guess_number,
                            MAX_ATTEMPTS - attempts);
                }
            }

            // If the player couldn't guess the number within the attempts
            if (attempts == MAX_ATTEMPTS) {
                System.out.printf("\nRound = %d\n", i);
                System.out.println("Attempts = 0");
                System.out.printf("The Random Number Is : %d\n\n", number);
            }
        }

        // Display total score after the game is over
        System.out.printf("Game Over. Total Score = %d\n", totalScore);
        scanner.close();
    }
}
