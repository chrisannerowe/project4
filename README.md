<!DOCTYPE html>
<html>

<head><title>Cheapo Mail</title></head>

<body>
	<?php
	
	$servername = "localhost";
	$username = "username";
	$password = "password";

	// Create connection
	$conn = new mysqli($servername, $username, $password);
	
	// Check connection
	if ($conn->connect_error) {
    		die("Connection failed: " . $conn->connect_error);
	} 

	// Create database
	$sql = "CREATE DATABASE myDB";
	if ($conn->query($sql) === TRUE) {
	    echo "Database created successfully";
	} else {
	    echo "Error creating database: " . $conn->error;
	}

	$conn->close();
	?>

	<table>
	<?php
	CREATE TABLE User(
		id INT(8) PRIMARY KEY,
		firstname VARCHAR(30) NOTNULL,
		lastname VARCHAR(30) NOTNULL,
		password VARCHAR(20) NOTNULL,
		username VARCHAR(20) NOTNULL
	)
	?>

	CREATE TABLE Message(
		id INT(8) PRIMARY KEY,
		body VARCHAR(150) NOTNULL,
		subject VARCHAR(15),
		user_id INT(8) NOTNULL,
		recipient_ids INT(100) NOTNULL
	)
	?>

	CREATE TABLE Message_id(
		id INT(8) PRIMARY KEY,
		message_id INT(8) NOTNULL,
		reader_id INT(8) NOTNULL,
		date TIMESTAMP
	)
	?>

	</table>

</body>
</html>
