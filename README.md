# Tour
Landing Page for Submitting your Details for Traveling

<!-- Code of Landing Page for Submitting the Pessangers Details -->
<!-- HTML Start -->


<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=5">
        <title>Travelling From</title>
        <link rel="stylesheet" href="Style.css" class="css">
    </head>
    <body>
        <img class="bg" src="bg.jpeg" alt="NIC Team">
        <div class= "container">
            <h1>Welcome to NIC Trip Form</h1>
            <p>Enter and submit your Cerdential for the conformation of the trip</p>
            <p class="submitmsg">Thanks for joining the trip with US</p>
            <form action="index.php" method="post">
                <input type="text" name="name" id="name" placeholder="Enter your name" />
                <input type="text" name="age" id="age" placeholder="Enter your age" />
                <input type="text" name="gender" id="gender" placeholder="Enter your gender" />
                <input type="text" name="email" id="email" placeholder="Enter your email" />
                <input type="text" name="phone" id="phone" placeholder="Enter your phone Number" />
                <textarea name="desc" id="desc" cols="30" rows="10"
                    placeholder="Enter any other Information here"></textarea>
                <input type="submit" class="btn" id="submit" name="submit" value="submit" />
            </form>
        </div>
        <script src="script.js"></script>
    </body>
    
</html>
<!-- HTML Code End -->

<!-- PHP Code Starts Here -->
<?php
 $server = "localhost";
 $username = "root";
 $passward = "";
$db="tour";
 $con = mysqli_connect($server, $username, $passward,$db);

 if(!$con){
     die("connection to this database failed due to" . mysqli_connect_error());
 }
 
  //echo "Success connecting to the database";
if(isset($_POST["submit"])){
$name = $_POST['name'];
$age = $_POST['age'];
$gender = $_POST['gender'];
$email = $_POST['email'];
$phone = $_POST['phone'];
$desc = $_POST['desc'];
$sql= "INSERT INTO `travelers_data` (`name`, `age`, `gender`, `email`, `phone`, `details`) VALUES ('$name', $age, '$gender', '$email', '$phone', '$desc')";
//echo $sql;

if (mysqli_query($con, $sql)) {
    // <p class="submitmsg">Thanks for joining the trip with US</p>;
    echo "New record created successfully";
  } else {
    echo "Error: " . $sql . "<br>" . mysqli_error($con);
  }

}
?>
<!-- PHP Code Ends Here -->
