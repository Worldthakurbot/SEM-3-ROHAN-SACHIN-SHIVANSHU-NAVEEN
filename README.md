import java.security.SecureRandom;

public class passwordgenerator {
    public static void main(String[] args) {
        int length = 12; // Specify the length of the password
        System.out.println("Generated Password: " + generatePassword(length));
    }
    public static String generatePassword(int length) {
        // Define character pools
        String upperCaseLetters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        String lowerCaseLetters = "abcdefghijklmnopqrstuvwxyz";
        String digits = "0123456789";
        String specialChars = "!@#$%^&*()-_+=<>?";
        String allChars = upperCaseLetters + lowerCaseLetters + digits + specialChars;
        SecureRandom random = new SecureRandom();
        StringBuilder password = new StringBuilder();
        // Ensure at least one character from each pool
        password.append(upperCaseLetters.charAt(random.nextInt(upperCaseLetters.length())));
        password.append(lowerCaseLetters.charAt(random.nextInt(lowerCaseLetters.length())));
        password.append(digits.charAt(random.nextInt(digits.length())));
        password.append(specialChars.charAt(random.nextInt(specialChars.length())));
        // Fill the rest of the password length with random characters
        for (int i = 4; i < length; i++) {
            password.append(allChars.charAt(random.nextInt(allChars.length())));
        }
        // Shuffle the password for better randomness
        return shuffleString(password.toString(), random);
    }
    private static String shuffleString(String input, SecureRandom random) {
        char[] chars = input.toCharArray();
        for (int i = chars.length - 1; i > 0; i--) {
            int j = random.nextInt(i + 1);
            // Swap characters
            char temp = chars[i];
            chars[i] = chars[j];
            chars[j] = temp;
        }
        return new String(chars);
    }
 }

  
