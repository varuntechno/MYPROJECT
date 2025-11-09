# MYPROJECT
MY FIRST IN JAVA PROJECT
package firstproject;

import java.util.Scanner;

/**
 * Calculator.java
 * A simple console application that performs basic arithmetic operations
 * (addition, subtraction, multiplication, division) on two numbers.
 *
 * To compile and run this program:
 * 1. Compile: javac Calculator.java
 * 2. Run: java Calculator
 */
public class Calculator {

    public static void main(String[] args) {
        // Initialize Scanner for user input
        Scanner scanner = new Scanner(System.in);

        System.out.println("--- Simple Console Calculator ---");

        try {
            // 1. Get the first number
            System.out.print("Enter the first number (A): ");
            double num1 = scanner.nextDouble();

            // 2. Get the operator
            System.out.print("Enter the operator (+, -, *, /): ");
            // We use next() to read the operator as a string
            String operator = scanner.next();

            // 3. Get the second number
            System.out.print("Enter the second number (B): ");
            double num2 = scanner.nextDouble();

            double result = 0;
            boolean validOperation = true;

            // 4. Perform the calculation based on the operator using a switch statement
            switch (operator) {
                case "+":
                    result = num1 + num2;
                    break;
                case "-":
                    result = num1 - num2;
                    break;
                case "*":
                    result = num1 * num2;
                    break;
                case "/":
                    // Handle division by zero error
                    if (num2 != 0) {
                        result = num1 / num2;
                    } else {
                        System.err.println("\nError: Division by zero is not allowed.");
                        validOperation = false;
                    }
                    break;
                default:
                    // Handle invalid operator error
                    System.err.println("\nError: Invalid operator entered. Please use +, -, *, or /.");
                    validOperation = false;
                    break;
            }

            // 5. Display the result if the operation was valid
            if (validOperation) {
                // Use printf to format the output to two decimal places
                System.out.printf("\nResult: %.2f %s %.2f = %.2f\n", num1, operator, num2, result);
            }

        } catch (java.util.InputMismatchException e) {
            // Catch error if the user enters non-numeric input for the numbers
            System.err.println("\nInput Error: Please ensure you enter valid numeric values for the numbers.");
        } catch (Exception e) {
            // Catch any other unexpected errors
            System.err.println("\nAn unexpected error occurred: " + e.getMessage());
        } finally {
            // Always close the scanner object to release system resources
            scanner.close();
        }

        System.out.println("---------------------------------");
    }
}
