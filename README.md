# Number_Guessing_Game
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        boolean playAgain = true;
        int totalAttempts = 0;
        int totalRounds = 0;
        final int maxAttempts = 10; // Limiting the maximum attempts to 10

        while (playAgain) {
            int randomNumber = random.nextInt(100) + 1;
            int attempts = 0;
            totalRounds++;

            System.out.println("Round " + totalRounds);
            System.out.println("Guess the number between 1 and 100.");

            boolean guessedCorrectly = false;
            while (!guessedCorrectly && attempts < maxAttempts) { // Adding condition to limit attempts
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;
                totalAttempts++;

                if (userGuess < randomNumber) {
                    System.out.println("Too low! Try again.");
                } else if (userGuess > randomNumber) {
                    System.out.println("Too high! Try again.");
                } else {
                    System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
                    guessedCorrectly = true;
                }
            }

            if (!guessedCorrectly && attempts == maxAttempts) { // Informing the user if max attempts reached
                System.out.println("Sorry, you've reached the maximum number of attempts (" + maxAttempts + ").");
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainInput = scanner.next().toLowerCase();
            playAgain = playAgainInput.equals("yes") || playAgainInput.equals("y");
        }

        System.out.println("Game over!");
        System.out.println("Total rounds played: " + totalRounds);
        System.out.println("Total attempts made: " + totalAttempts);

        scanner.close();
    }
}
