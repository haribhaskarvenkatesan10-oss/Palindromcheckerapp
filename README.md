import java.util.Scanner;
import java.util.Stack;

public class Palindromcheckerapp {

    public static boolean isBasicPalindrome(String input) {
        String reversed = "";

        for (int i = input.length() - 1; i >= 0; i--) {
            reversed += input.charAt(i);
        }

        return input.equals(reversed);
    }

    public static boolean isCaseInsensitivePalindrome(String input) {
        String lowerInput = input.toLowerCase();
        String reversed = "";

        for (int i = lowerInput.length() - 1; i >= 0; i--) {
            reversed += lowerInput.charAt(i);
        }

        return lowerInput.equals(reversed);
    }

    public static boolean isCleanPalindrome(String input) {
        String cleaned = input.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        String reversed = "";

        for (int i = cleaned.length() - 1; i >= 0; i--) {
            reversed += cleaned.charAt(i);
        }

        return cleaned.equals(reversed);
    }

    public static boolean isStackPalindrome(String input) {
        String cleaned = input.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < cleaned.length(); i++) {
            stack.push(cleaned.charAt(i));
        }

        for (int i = 0; i < cleaned.length(); i++) {
            if (cleaned.charAt(i) != stack.pop()) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n===== Palindrome Checker App =====");
            System.out.println("1. Basic Palindrome Check");
            System.out.println("2. Case-Insensitive Check");
            System.out.println("3. Ignore Spaces & Special Characters");
            System.out.println("4. Stack-Based Palindrome Check");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            choice = scanner.nextInt();
            scanner.nextLine();

            if (choice >= 1 && choice <= 4) {
                System.out.print("Enter a string: ");
                String input = scanner.nextLine();

                boolean result = false;

                switch (choice) {
                    case 1:
                        result = isBasicPalindrome(input);
                        break;
                    case 2:
                        result = isCaseInsensitivePalindrome(input);
                        break;
                    case 3:
                        result = isCleanPalindrome(input);
                        break;
                    case 4:
                        result = isStackPalindrome(input);
                        break;
                }

                if (result) {
                    System.out.println("Result: The string IS a palindrome.");
                } else {
                    System.out.println("Result: The string is NOT a palindrome.");
                }
            }

        } while (choice != 5);

        System.out.println("Exiting Palindrome Checker App. Goodbye!");
        scanner.close();
    }
}
