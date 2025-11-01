# Login-System-
A simple yet effective and efficient login system allowing user to input data 

import java.util.Scanner;

public class AlonzoLoginSystem {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        String[][] users = new String[100][2]; // [username][password]
        int userCount = 0;
        int choice;

        do {
            System.out.println("==== LOGIN SYSTEM ====");
            System.out.println("[1] Login");
            System.out.println("[2] Register");
            System.out.println("[3] Exit");
            System.out.print("Choose an option: ");
            choice = input.nextInt();
            input.nextLine(); 

            if (choice == 1) { 
                // LOGIN
                System.out.print("Enter username: ");
                String username = input.nextLine();
                System.out.print("Enter password: ");
                String password = input.nextLine();

                boolean found = false;
                for (int i = 0; i < userCount; i++) {
                    if (users[i][0].equals(username) && users[i][1].equals(password)) {
                        System.out.println("Hello, " + username + "!");
                        found = true;
                        break;
                    }
                }

                if (!found) {
                    System.out.println("Invalid username or password!");
                }

            } else if (choice == 2) { 
                // REGISTER
                System.out.print("Enter new username: ");
                String newUser = input.nextLine();

                boolean exists = false;
                for (int i = 0; i < userCount; i++) {
                    if (users[i][0].equals(newUser)) {
                        exists = true;
                        break;
                    }
                }

                if (exists) {
                    System.out.println("Username already exists!");
                } else {
                    System.out.print("Enter password: ");
                    String newPass = input.nextLine();
                    System.out.print("Confirm password: ");
                    String confirm = input.nextLine();

                    if (!newPass.equals(confirm)) {
                        System.out.println("Passwords do not match!");
                    } else {
                        users[userCount][0] = newUser;
                        users[userCount][1] = newPass;
                        userCount++;
                        System.out.println("Registration successful!");
                    }
                }

            } else if (choice == 3) { 
                // EXIT
                System.out.println("Goodbye!");
            } else {
                System.out.println("Invalid choice!");
            }

            System.out.println(); // space for next menu
        } while (choice != 3);

        input.close();
    }
}
