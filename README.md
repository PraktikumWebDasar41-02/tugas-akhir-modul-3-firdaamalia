# tugas-akhir-modul-3-firdaamalia
tugas-akhir-modul-3-firdaamalia created by GitHub Classroom

<?php

session_start();
if(isset($_SESSION["username"]) && isset($_SESSION["password"])) {
}
?>
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
		<form action="knk.php" method="POST" enctype="multipart/form-data">
			<table>
				<tr>
			<h3><i> ====Firda Amalia==== </i></h3><br><br>
				<tr>
					<img alt="gambar koala" src="gb.jpg" height="150" width="210" />
					<img alt="gambar koala" src="bg.jpg" height="150" width="210" /><br>
				</tr>
				<tr>
					<img alt="gambar koala" src="bg.jpg" height="150" width="210" />
					<img alt="gambar koala" src="gb.jpg" height="150" width="210" /><br>
				</tr>
						<tr>
							<td><b>Upload Foto : </b></td>
        				</tr>	
        				<tr>
                           <td> <input type="file" name="fileToUpload" id="fileToUpload"></td><br>
                            <td> <input type="submit" value="Upload Image" name="submit"></td>
                         </tr>
						
					</table><br>
					<a href="lgt1.php">Logout</a>
		</body>
</html>
</form>



<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8 ">
	<title>TA 3 Firda</title>
</head>
<body>
		<h3>LOGIN</h3>
		<form action="fr.php" method="POST">
			<table>
		<tr>
			<td>Username</td>
			<td><input type="username" name="username" placeholder="username"></td>
		</tr>
		<tr>
			<td>Password</td> 
			<td><input type="password" name="password" placeholder="password"></td>
		</tr>
		<tr>
			<td></td>
			<td><input type="submit" name="submit" value="submit" class="form1.php">
			 <input type="reset" value="Cancel"></td>
		</tr>
		</table>
		</form>
</body>
</html>


<?php  
 $host = "localhost";  
 $username = "root";  
 $password = "";  
 $db = "tafirda";  
 $conn = mysqli_connect($host,$username,$password, $db); 
 ord("koneksi gagal") ;
 try{
 	$pdo = new PDO("mysql:host={$host}; dbname={$db};", $username,$password);
 	$pdo -> setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
 }	
 catch (PDOException $e){
 	print "koneksi atau query bermasalah : " . $e -> getMessage() ."<br>";
 	die();
 }


 	if (isset($POST['submit'])){
 	$user = $_POST['namauser'];  
 	$pass = $_POST['password'];  
 	$gbr = $_FILES['gambar']['name'];
 	$tmp_name = $_FILES['gambar']['tmp_name'];
 	$dir_foto = "file/";
 	$target_foto = $dir_foto . $gbr;

 	
	 	$query = $pdo -> prepare("INSERT INTO tabelfirda VALUES ('$user' , '$pass',  '$gbr')");
	 	$query -> execute();
	 }
?>


<?php 
session_start();
session_destroy();
header("Location: log1.php");
?>



