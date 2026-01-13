---
updated_at: 2025-10-08T15:58:39.514+05:30
edited_seconds: 170
---
```
What is the full form of JDBC?
a.
b.
c.
d.
Java Database Connectivity
Java Data Code
Java Data Communication
Java Development Connectivity

Fill in the missing code to establish a connection to a MySQL database.
import java. sql.*;
public class JDBCExarr.p1e {
public static void main (String [J args) {
try {
Class . forName ( " com.mysql . c j . j dbc . Driver ;
// Establish Connection
Connection connection
= // INSERT CODE HERE;
System. out . print In ("Connected to the database.
connection. close ( ) ;
) catch (Exception e) {
e . printstackTrace ( ) ;
What should replace // INSERT CODE KEFE ?
a.
b.
c.
d.
DriverManager.connect("mysql:localhost:mydb", "user", "password");
DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "user", "password");
Connection.get("jdbc:mysql://localhost:3306/mydb", "user", "password");
Driver.connect("jdbc:mysql://localhost:mydb", "user"
password");
Identify the error in the following code and select the corrected statement:
import java. SAI. * •
public class ResultSetExamp1e {
public static void main (String [J args) throws SQLException {
Connection connection —
DriverManager . getConnection ("jdbc : mysql : / / localhost : 330 é/mydb" ,
" user'
"password") ;
= connection. createStatement ( ) ;
Statement stmt
= stmt . execute ("SELECT FROM users"); // Error
ResultSet rs
while (r s. next ( ) )
System. out . print In (rs . getstring ( "username") ) ;
connection. close ( ) ;
What is the correct statement to replace the line with error (stmt. execute ( SELECT * FROM
users
a.
b.
c.
d.
ResultSet rs = stmt.executeQuery("SELECT * FROM users");
ResultSet rs = stmt.runQuery("SELECT * FROM users");
ResultSet rs = stmt.execute("users SELECT * FROM");
ResultSet rs = stmt.fetch("SELECT * FROM users");
Consider the following code.
import java.
public class DisplayProducts {
public static void main (String [ ] args) {
try {
'Zonnecticn conn
DriverUanager . getConnection ( " clbc : mysgl : / / localhost : 3 3 ü € / store " ,
"pass");
conn. createStatement ( ) ;
Statement stmt
" root " ,
ResultSet r 3
= stmt . executeQuery ("SELECT name FROM products") ;
while (r s. next ( ) )
System. out . print In (rs .getString ("name") ) ;
conn.close ( ) ;
} catch (SQLException e) {
e . print StackTrace ( ) ;
What will the above Java program output if the database contains a table products with a column
name and three rows: Laptop, Phone, and Tablet?
a.
b.
c.
d.
Compilation Error
Runtime Error
Laptop
Phone
Tablet
No Output

Complete the following code to insert a new user into a users table.
import java. sgl.*•
public class Insert User {
public static void main (String[] args) {
try {
Connection conn
DriverUanager . getconnection ( " dbc : mysgl : / / localhost : 33 ü € / myclb" ,
" root " ,
" password") ;
String query
"INSERT INTO users (username, email) VALVES
= // INSERT CODE HERE
PreparedStatement pstmt
pstmt . setString (1,
" i ohn doe") ;
pstmt . setstring (2,
"j ühn@example . corn") ;
pstmt . executeVpdate ( ) ;
conn. close ( ) ;
) catch (SQLException e) {
e. print Stackcrace ( ) ;
What should replace // INSERT CODE
a.
b.
c.
d.
conn.createStatement(query);
conn.prepareStatement(query);
conn.execute(query);
conn.runStatement(query);

Which of the following SQL operations can be executed using the executeUpdate method in JDBC?
l.
lv.
a.
b.
c.
d
INSERT INTO users (id, name) VALUES (1, 'Alice');
UPDATE users SET name:' Bob' WHERE id=l;
DELETE FROM users WHERE id=l;
SELECT * FROM users;
l, II, and Ill
Only I and II
Only I
l, II, Ill and IV

What is the purpose of the DriverManager class in JDBC?
a.
b.
c.
d.
To manage database connections.
To execute SQL queries.
To fetch data from a database.
To represent a database record.

How do you establish a connection to a database using JDBC?
a.
b.
c.
d.
By creating an instance of the Connection interface
By using the DriverManager.getConnection() method
By implementing the Connection interface
By extending the Connection class
Which method executes a simple query and returns a single Result Set object?
a.
b.
c.
d.
executeQuery()
executelJpdate()
execute()
run()
Which package in Java contains the classes and interfaces for JDBC?
a.
b.
c.
d.
java.sql
java.io
java.db
java.net


