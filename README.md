# filehandling
EXPLANATION:                                                                                                                                                                                                   This Java program demonstrates basic file handling using FileWriter, BufferedWriter, FileReader, and BufferedReader to write and read employee data to and from a file named employees.txt. The program begins in the main method, where it first calls writeToFile() to save hardcoded employee records in a comma-separated format. It uses BufferedWriter to write each employee’s ID, name, department, designation, and salary to the file, placing each record on a new line. After writing the data, the program calls readFromFile() to read and display the contents of the file. This method uses BufferedReader to read the file line by line, splits each line into fields using the comma as a delimiter, and then prints the employee information in a well-formatted table. The use of buffered streams improves performance, and the try-with-resources syntax ensures that file resources are closed automatically. This program provides a simple and clear example of file input/output operations in Java and how data can be structured, stored, and retrieved efficiently.
CODE:                                                                                                                                                                                                             import java.io.*;

public class FileHandlingExample {

    public static void main(String[] args) {
        String fileName = "employees.txt";

        // Writing to the file
        writeToFile(fileName);

        // Reading from the file
        readFromFile(fileName);
    }

    // Method to write employee details to a file
    public static void writeToFile(String fileName) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName))) {
            writer.write("1001,Rahul,Accounts,Clerk,29000");
            writer.newLine();
            writer.write("1002,Priya,HR,Manager,55000");
            writer.newLine();
            writer.write("1003,Sam,IT,Developer,40000");
            System.out.println("Employee data written to file successfully.");
        } catch (IOException e) {
            System.out.println("An error occurred while writing to the file.");
            e.printStackTrace();
        }
    }

    // Method to read and display employee details from a file
    public static void readFromFile(String fileName) {
        try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
            String line;
            System.out.printf("%-10s %-10s %-12s %-12s %s%n", "Emp ID", "Name", "Department", "Designation", "Salary");
            System.out.println("--------------------------------------------------------------");
            while ((line = reader.readLine()) != null) {
                String[] data = line.split(",");
                System.out.printf("%-10s %-10s %-12s %-12s %s%n", data[0], data[1], data[2], data[3], data[4]);
            }
        } catch (IOException e) {
            System.out.println("An error occurred while reading from the file.");
            e.printStackTrace();
        }
    }
}
