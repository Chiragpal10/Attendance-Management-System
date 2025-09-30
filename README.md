# Attendance System

This is a simple Attendance Management System built with Python and MySQL.

## Features

- Add students and batches
- Mark attendance for single or all students
- View attendance records
- Generate attendance reports per batch
- Delete student records

## Requirements

- Python 3.x
- `pymysql` package (`pip install pymysql`)
- MySQL database with schema:

```sql
CREATE TABLE batch (
    bid INT AUTO_INCREMENT PRIMARY KEY,
    BName VARCHAR(100)
);

CREATE TABLE student (
    sid INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    bid INT,
    FOREIGN KEY (bid) REFERENCES batch(bid)
);

CREATE TABLE attendance (
    aid INT AUTO_INCREMENT PRIMARY KEY,
    sid INT,
    bid INT,
    status ENUM('present','absent'),
    date DATE,
    FOREIGN KEY (sid) REFERENCES student(sid),
    FOREIGN KEY (bid) REFERENCES batch(bid)
);
