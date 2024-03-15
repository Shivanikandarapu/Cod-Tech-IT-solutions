/**
 * Student Grade Management System
 * This program allows users to manage student records, including adding, deleting, updating, and displaying student information such as name, roll number, marks, total marks, average percentage, and grade.
 */
package Task_7;

import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    private static Scanner scanner = new Scanner(System.in);
    private static ArrayList<Student> studList = new ArrayList<Student>();

    /**
     * The main method serves as the entry point for the Student Grade Management System.
     * It presents a menu to the user with options to perform various operations on student records.
     * The user can continue using the system until choosing to exit.
     * @param args Command-line arguments (not used)
     */
    public static void main(String arg[]) {
        System.out.println("\n\t\tWelcome to Student Grade Management System");

        int ch;
        do {
            System.out.println("\n\n1: Add Student");
            System.out.println("2: Delete Student");
            System.out.println("3: Update Student");
            System.out.println("4: Display Student");
            System.out.println("5: Exit");
            System.out.print("Enter your choice: ");
            ch = scanner.nextInt();
            switch (ch) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    deleteStudent();
                    break;
                case 3:
                    updateStudent();
                    break;
                case 4:
                    displayStudent();
                    break;
                case 5:
                    System.out.println("\nGoodbye! Thank you for using Student Grade Management System");
                    break;
            }
        } while (ch != 5);
    }

    /**
     * Adds a new student record to the system.
     * Prompts the user to enter the student's name, roll number, number of subjects, and marks for each subject.
     * Calculates the total marks, average percentage, and grade based on the entered marks.
     * Stores the student record in the ArrayList.
     */
    private static void addStudent() {
        // Prompt user to enter student details
        // Calculate total marks, average percentage, and grade
        // Add student record to the ArrayList
    }

    /**
     * Updates an existing student record in the system.
     * Prompts the user to enter the roll number of the student whose record needs to be updated.
     * Allows the user to update the student's name and roll number.
     */
    private static void updateStudent() {
        // Prompt user to enter existing student's roll number
        // Allow user to update student's name and roll number
    }

    /**
     * Displays all student records stored in the system.
     * Prints details such as name, roll number, number of subjects, total marks, average percentage, and grade for each student.
     */
    private static void displayStudent() {
        // Iterate through the ArrayList and print student details
    }

    /**
     * Deletes an existing student record from the system.
     * Prompts the user to enter the roll number of the student whose record needs to be deleted.
     */
    private static void deleteStudent() {
        // Prompt user to enter existing student's roll number
        // Delete student record from the ArrayList
    }
}
