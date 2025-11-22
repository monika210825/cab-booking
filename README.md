A simple console-based Cab Booking System implemented using:

Java 8

Hibernate ORM 5.6

MySQL Database

Maven Project

DAO Layer (User, Cab, Booking)

Console Menu Interface

📁 Project Overview
Section	Details
Project Type	Console Application
Backend	Java 8, Hibernate ORM
Database	MySQL
ORM	Hibernate (XML config)
Build Tool	Maven
Architecture	DAO + Model + Service + Console UI
Tables	users, cabs, bookings

📁 Folder Structure
Path	Description
src/main/java/com/cabbooking/	Main application
src/main/java/com/cabbooking/models/	Entity classes
src/main/java/com/cabbooking/dao/	DAO classes + HibernateUtil
src/main/resources/hibernate.cfg.xml	Hibernate configuration file
database/database.sql	SQL schema file
pom.xml	Maven dependencies

⚙️ Software Requirements
Software	Version
Java JDK	8 (important)
Apache Maven	3.X
MySQL Server	5.7 / 8.0
Eclipse/IntelliJ	Any version with Maven support

📦 Maven Dependencies

Add this to your pom.xml:

Dependency	Purpose
Hibernate Core	ORM engine
Javax Persistence API	Annotations (@Entity, @Table)
MySQL Connector/J	Database driver
SLF4J Simple	Logging
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-core</artifactId>
    <version>5.6.15.Final</version>
</dependency>

<dependency>
    <groupId>javax.persistence</groupId>
    <artifactId>javax.persistence-api</artifactId>
    <version>2.2</version>
</dependency>

<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>

<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-simple</artifactId>
    <version>2.0.9</version>
</dependency>

🗄️ Database Configuration

Create Database:

CREATE DATABASE cabdb;
USE cabdb;


Tables:

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100),
  phone VARCHAR(20)
);

CREATE TABLE cabs (
  id INT AUTO_INCREMENT PRIMARY KEY,
  number_plate VARCHAR(20),
  driver_name VARCHAR(100),
  model VARCHAR(100),
  available BOOLEAN DEFAULT TRUE
);

CREATE TABLE bookings (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  cab_id INT,
  pickup VARCHAR(255),
  dropoff VARCHAR(255),
  status VARCHAR(50),
  FOREIGN KEY (user_id) REFERENCES users(id),
  FOREIGN KEY (cab_id) REFERENCES cabs(id)
);

⚙️ Hibernate Configuration (hibernate.cfg.xml)
Property	Value
Hibernate Dialect	MySQL8Dialect
Driver Class	com.mysql.cj.jdbc.Driver
DB URL	jdbc:mysql://localhost:3306/cabdb
Username	root
Password	root
hbm2ddl.auto	update

File:

<property name="hibernate.connection.url">jdbc:mysql://localhost:3306/cabdb</property>
<property name="hibernate.connection.username">root</property>
<property name="hibernate.connection.password">root</property>
<property name="hbm2ddl.auto">update</property>

🚀 How to Import Project in Eclipse
Step	Description
1	Open Eclipse
2	Go to File → Import
3	Select Maven → Existing Maven Project
4	Select project folder
5	Click Finish
6	Right-click project → Maven → Update Project (Enable Force Update)
7	Right-click project → Build Path → Configure Build Path
8	Ensure JRE System Library: JavaSE-1.8
▶️ How to Run the Application
Step	Action
1	Open Main.java in com.cabbooking package
2	Right-click → Run As → Java Application
3	Console menu appears

You will see:

===== CAB BOOKING SYSTEM =====
1. Add User
2. List Users
3. Add Cab
4. List Cabs
5. Book Cab
6. View Bookings
7. Delete Booking
8. Exit


Select options using numbers.

📚 What the Application Does
Feature	Description
Add User	Stores new user in DB
List Users	Shows all users
Add Cab	Stores cab info
List Cabs	Shows cabs + availability
Book Cab	Assigns cab to user + marks cab unavailable
View Bookings	Shows all bookings with user + cab
Delete Booking	Removes booking + frees cab
Exit	Closes Hibernate session
🛠️ Troubleshooting
Issue	Solution
Unknown database 'cabdb'	Create DB manually using SQL
The import javax.persistence cannot be resolved	Run Maven → Update Project
Arrow case not supported	Use Java 8 switch syntax
Method shutdown() undefined	Use correct HibernateUtil.java
Hibernate shows connection pool warning	Normal (built-in pool)
