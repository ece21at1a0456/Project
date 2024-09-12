import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        // Set the range and max attempts
        int lowerBound = 1;
        int upperBound = 100;
        int maxAttempts = 5;
        
        // Generate the random number to be guessed
        int numberToGuess = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
        int attempts = 0;
        boolean hasWon = false;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("Guess a number between " + lowerBound + " and " + upperBound + ".");
        System.out.println("You have " + maxAttempts + " attempts to guess the correct number.");

        // Start the guessing loop
        while (attempts < maxAttempts) {
            System.out.print("Enter your guess: ");
            int guess = scanner.nextInt();
            attempts++;

            if (guess == numberToGuess) {
                hasWon = true;
                break;
            } else if (guess > numberToGuess) {
                System.out.println("Too High!");
            } else {
                System.out.println("Too Low!");
            }

            System.out.println("Attempts remaining: " + (maxAttempts - attempts));
        }

        // Game outcome
        if (hasWon) {
            System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
        } else {
            System.out.println("You've used all attempts! The correct number was " + numberToGuess + ".");
        }

        scanner.close();
    }
}

