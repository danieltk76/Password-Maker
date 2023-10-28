import javax.swing.JOptionPane;
import java.util.Random;
import java.io.File;
import java.io.PrintWriter;
import java.io.FileWriter;
import java.io.IOException;

public class passwordMaker {
    public static void main(String[] args) throws IOException {
        String upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        String lower = "abcdefghijklmnopqrstuvwxyz";
        String num = "0123456789";
        String specialChars = "!@#$%^&*()_+";

        // Check if the file exists and is empty
        File file = new File("passwords.txt");
        

        FileWriter fw = new FileWriter(file, true);
        PrintWriter pw = new PrintWriter(fw);

        String combination = upper + lower + num + specialChars;
        Random r = new Random();

        String userSelect = JOptionPane.showInputDialog("Would you like a password?");

        if (userSelect != null && userSelect.equalsIgnoreCase("Yes")) {
            String userName = JOptionPane.showInputDialog("What is your name? ");
            String passwordLen = JOptionPane.showInputDialog("How long do you want your password to be?");
            int len = Integer.parseInt(passwordLen);

            char[] password = new char[len];

            for (int i = 0; i < len; i++) {
                password[i] = combination.charAt(r.nextInt(combination.length()));
            }

            String passwordStrength = "";
            String hackability = "";
            if (len < 7) {
                passwordStrength = "Weak";
                hackability = "possible";
                
            } else if (len > 8 && len < 20) {
                passwordStrength = "Solid";
                hackability = "unlikely";
            } else if (len > 21) {
                passwordStrength = "Strong";
                hackability = "impossible";
            }

            // Print the header only if the file is empty
            boolean fileExists = file.exists();
            boolean fileIsEmpty = !fileExists || file.length() == 0;


            // Print the header only if the file is empty
            if (fileIsEmpty) {
                pw.printf("%-19s %-19s %-19s %-19s%n", "|Name|", "|Password Generated|", "|Security Score|", "|Hackability|");
            }

            
            // Format and print the data centered under specific categories
            pw.printf("%-20s %-20s %-20s %-20s%n", userName, new String(password), passwordStrength, hackability);
            pw.close();

            JOptionPane.showMessageDialog(null, "New password: " + new String(password), "Password Generator", JOptionPane.INFORMATION_MESSAGE);
        }
    }
}



