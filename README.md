# student-management-system-java1
Console based java project using JDBC and mysql

Student Management System

Description

Student Management System is a console-based Java application designed to manage student records efficiently.
It uses Core Java and JDBC to store and retrieve data from a MySQL database.

Technologies Used

Core Java

JDBC

MySQL

Features

Add new student details

View student records

Store data permanently using database

Concepts Used

Object-Oriented Programming (OOP)

Encapsulation

JDBC Connectivity

Exception Handling

Database Details

Database: studentdb

Table: student

How to Run

1. Create database and table in MySQL


2. Update database username and password in DBConnection.java


3. Run MainApp.java
Conversation opened. 1 unread message. 

Skip to content
Using Gmail with screen readers
1 of 49
(no subject)
Inbox

Manireethika Burukala <manireethikab@gmail.com>
12:30 (1 minute ago)
to me

import java.sql.*;
import java.util.Scanner;

public class StudentManagementSystem {
    static Connection getConnection() throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        return DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
        );
    }
    static void addStudent(int id, String name, int age) throws Exception {
        Connection con = getConnection();
        PreparedStatement ps =
                con.prepareStatement("INSERT INTO student VALUES (?,?,?)");
                ps.setInt(1, id);
        ps.setString(2, name);
        ps.setInt(3, age);
        ps.executeUpdate();
        con.close();
        System.out.println("Student Added Successfully");
    }

 static void viewStudents() throws Exception {
        Connection con = getConnection();
        Statement st = con.createStatement();
        ResultSet rs = st.executeQuery("SELECT * FROM student");
 System.out.println("ID NAME AGE");
        while (rs.next()) {
            System.out.println(
                    rs.getInt("id") + " " +
                    rs.getString("name") + " " +
                    rs.getInt("age")
            );
        }
        con.close();
    }
    public static void main(String[] args) throws Exception {
  Scanner sc = new Scanner(System.in);

 System.out.println("Enter Student ID:");
        int id = sc.nextInt();

 System.out.println("Enter Student Name:");
        String name = sc.next();

 System.out.println("Enter Student Age:");
        int age = sc.nextInt();

  addStudent(id, name, age);
        viewStudents();
    }
}


Author

B.Tech (ECE)
Java Developer Fresher
