import java.util.Scanner;

public class Calculator {
    
    // Method to add two numbers
    public static double add(double num1, double num2) {
        return num1 + num2;
    }
    
    // Method to subtract two numbers
    public static double subtract(double num1, double num2) {
        return num1 - num2;
    }
    
    // Method to multiply two numbers
    public static double multiply(double num1, double num2) {
        return num1 * num2;
    }
    
    // Method to divide two numbers
    public static double divide(double num1, double num2) {
        if (num2 == 0) {
            System.out.println("Error: Cannot divide by zero!");
            return 0;
        }
        return num1 / num2;
    }
    
    // Main method to run the calculator
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean continueCalculation = true;
        
        System.out.println("=== Simple Calculator ===\n");
        
        while (continueCalculation) {
            try {
                // Input first number
                System.out.print("Enter first number: ");
                double num1 = scanner.nextDouble();
                
                // Input operator
                System.out.print("Enter operator (+, -, *, /): ");
                char operator = scanner.next().charAt(0);
                
                // Input second number
                System.out.print("Enter second number: ");
                double num2 = scanner.nextDouble();
                
                double result = 0;
                boolean validOperation = true;
                
                // Perform the operation based on operator
                switch (operator) {
                    case '+':
                        result = add(num1, num2);
                        break;
                    case '-':
                        result = subtract(num1, num2);
                        break;
                    case '*':
                        result = multiply(num1, num2);
                        break;
                    case '/':
                        result = divide(num1, num2);
                        break;
                    default:
                        System.out.println("Invalid operator! Please use +, -, *, or /\n");
                        validOperation = false;
                }
                
                // Display result
                if (validOperation) {
                    System.out.println("Result: " + num1 + " " + operator + " " + num2 + " = " + result + "\n");
                }
                
                // Ask if user wants to continue
                System.out.print("Do you want to perform another calculation? (yes/no): ");
                String response = scanner.next().toLowerCase();
                
                if (!response.equals("yes") && !response.equals("y")) {
                    continueCalculation = false;
                    System.out.println("Thank you for using the calculator!");
                }
                
            } catch (Exception e) {
                System.out.println("Invalid input! Please enter valid numbers.\n");
                scanner.nextLine(); // Clear the input buffer
            }
        }
        
        scanner.close();
    }
}
