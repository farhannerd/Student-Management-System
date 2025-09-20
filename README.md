# Student Management System

A simple desktop application built with Java Swing and MySQL for managing student records. This project demonstrates basic CRUD operations with a graphical user interface.

## Features

- **Add Students**: Register new students with their details
- **View Students**: Display all students in a table format
- **Update Students**: Modify existing student information
- **Delete Students**: Remove students from the database
- **Form Validation**: Ensure data integrity with input validation

## Screenshots

![Student Management System GUI](screenshot.png)
*Main interface showing student list and input form*

## Technologies Used

- **Java SE** - Core programming language
- **Swing/AWT** - GUI framework
- **MySQL** - Database management system
- **JDBC** - Database connectivity
- **Linux** - Development and deployment environment

## Prerequisites

Before running this application, make sure you have the following installed:

- Java Development Kit (JDK 8 or higher)
- MySQL Server
- MySQL JDBC Driver (included in `lib/` directory)

## Database Setup

1. **Install and start MySQL:**
   ```bash
   sudo systemctl start mysql
   sudo systemctl enable mysql
   ```

2. **Create database and user:**
   ```sql
   CREATE DATABASE student_db;
   USE student_db;
   
   CREATE TABLE students (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       email VARCHAR(100) UNIQUE NOT NULL,
       age INT NOT NULL,
       course VARCHAR(50) NOT NULL
   );
   
   CREATE USER 'student_user'@'localhost' IDENTIFIED BY 'password123';
   GRANT ALL PRIVILEGES ON student_db.* TO 'student_user'@'localhost';
   FLUSH PRIVILEGES;
   ```

## Installation and Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/student-management-system.git
   cd student-management-system
   ```

2. **Download MySQL JDBC Driver** (if not included):
   ```bash
   wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-j-8.0.33.tar.gz
   tar -xzf mysql-connector-j-8.0.33.tar.gz
   cp mysql-connector-j-8.0.33/mysql-connector-j-8.0.33.jar lib/
   ```

3. **Make scripts executable:**
   ```bash
   chmod +x compile.sh run.sh
   ```

## How to Run

### Option 1: Using Scripts (Recommended)

```bash
# Compile the project
./compile.sh

# Run the application
./run.sh
```

### Option 2: Manual Compilation

```bash
# Compile
javac -cp "lib/mysql-connector-j-8.0.33.jar" -d out src/*.java

# Run
java -cp "out:lib/mysql-connector-j-8.0.33.jar" StudentManagementGUI
```

## Project Structure

```
student-management-system/
├── src/                          # Source code files
│   ├── DatabaseConnection.java   # Database connection utility
│   ├── Student.java             # Student model class
│   ├── StudentDAO.java          # Data Access Object
│   └── StudentManagementGUI.java # Main GUI application
├── lib/                         # External libraries
│   └── mysql-connector-j-*.jar  # MySQL JDBC driver
├── out/                         # Compiled class files (auto-generated)
├── compile.sh                   # Compilation script
├── run.sh                      # Execution script
├── .gitignore                  # Git ignore rules
└── README.md                   # Project documentation
```

## Usage

1. **Launch the application** using the run script or manual commands
2. **Add a new student** by filling out the form and clicking "Add Student"
3. **View all students** in the table display
4. **Update a student** by selecting a row, modifying the form, and clicking "Update Student"
5. **Delete a student** by selecting a row and clicking "Delete Student"
6. **Clear the form** using the "Clear Form" button
7. **Refresh the data** using the "Refresh" button

## Database Configuration

The database connection settings are located in `DatabaseConnection.java`:

```java
private static final String URL = "jdbc:mysql://localhost:3306/student_db";
private static final String USERNAME = "student_user";
private static final String PASSWORD = "password123";
```

Modify these settings if you use different database credentials.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Future Enhancements

- [ ] Add search and filter functionality
- [ ] Implement data export (CSV, PDF)
- [ ] Add student photo upload feature
- [ ] Create user authentication system
- [ ] Add data backup and restore features
- [ ] Implement input validation improvements
- [ ] Add batch operations (import/export multiple students)

## Troubleshooting

### Common Issues

1. **Database Connection Failed**
   - Ensure MySQL is running: `sudo systemctl status mysql`
   - Verify database credentials in `DatabaseConnection.java`
   - Check if the database and user exist

2. **ClassNotFoundException**
   - Ensure MySQL JDBC driver is in the `lib/` directory
   - Check the classpath in compilation and execution commands

3. **GUI Not Displaying (SSH)**
   - Use X11 forwarding: `ssh -X username@hostname`
   - Set DISPLAY variable: `export DISPLAY=:0`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com

## Acknowledgments

- Built as a learning project to understand Java GUI development and database integration
- Thanks to the Java and MySQL communities for excellent documentation
