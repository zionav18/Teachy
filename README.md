<?php
     include('config.php');
?>
<!DOCTYPE html>
<html dir="rtl" lang="ar>
<head>
    <head>
    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
     <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Acme Web Deisgn | Search Knowlage</title>
    <link rel="stylesheet" href="./css/style.css">

    <script>
  $(document).ready(function(){
  $("#search").on("keyup", function() {
    var value = $(this).val().toLowerCase();
    $("#myTable tr").filter(function() {
      $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1)
    });
  });
});
    </script>
  </head>
  
  <body>
    <header>

      <div class="container">

         <div id="branding">
          <img src="./img/logo.png">
         </div>

         <div id="branding2">
          <a href="#">
            <img src="./img/p.png">
          </a> 
        </div>

          <ul class="nav">
            <li> <a href="#">שיעורים פרטיים</a></li>
            <li>  <a href="index.html">שיתוף ידע</a></li>
            <li class="current"> <a href="#">חיפוש ידע</a></li>
          </ul>

      </div>
    </header>
    
    <br>
    <input class="search" type="text" placeholder="חפש קןרס"><br>
    <form action="upload.php" method="post">
    <?php

    $degreeDB = $_POST['degree'];
    $yearDB =  $_POST['year'];
      
      $result=mysqli_query($db,"SELECT * from courses where Degree='$degreeDB' and Year='$yearDB'");
      ?>

       <table>
    <tr> 
      <th>שם הקורס</th>
     
    </tr>
    <tbody id="myTable">
<?php
      if ($result->num_rows>0){ 
                while($row=$result->fetch_assoc()){
                    $temp=$row['id'];
                    echo $temp;
                    echo '<tr><td>'.$row['name'].'</td>';
                    echo '<td><button class="button_1" type="submit" value="'.$temp.'" name="add">הוסף למאגר ידע</button>';
                    echo '<button class="button_1" type="submit" value="'.$temp.'" name="add"> רישום כמורה פרטי</button></td></tr>';

                }
            }

    ?>
  </tbody>
  </table>
</form>
  <footer>
          <ul class="nav">
            <li> <a href="FAQ.html">שאלות ותשובות</a></li>
            <li> <a href="#">עלינו</a></li>
          </ul>
    </footer>


</body>
</html>



<?php
     include('config.php');
?>


<!DOCTYPE html>
<html>
<head>
    <head>
    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Acme Web Deisgn | Search Knowlage</title>
    <link rel="stylesheet" href="./css/style.css">


    
  </head>
  
  <body>
    <header>

      <div class="container">

         <div id="branding">
          <img src="./img/logo.png">
         </div>

         <div id="branding2">
          <a href="#">
            <img src="./img/p.png">
          </a> 
        </div>

          <ul class="nav">
            <li> <a href="#">שיעורים פרטיים</a></li>
            <li>  <a href="index.html">שיתוף ידע</a></li>
            <li class="current"> <a href="#">חיפוש ידע</a></li>
          </ul>

      </div>
    </header>

    <?php

    $degreeDB = $_POST['degree'];
    $yearDB =  $_POST['year'];
      
      $result=mysqli_query($db,"SELECT * from courses where Degree='$degreeDB' and Year='$yearDB'");
      ?>

       <table>
    <tr> 
      <th>שם הקורס</th>
     
    </tr>
<?php
      if ($result->num_rows>0){ 
                while($row=$result->fetch_assoc()){
                    echo '<tr><td>'.$row['name'].'</td>';
                    echo '<td><button type="button">סיכומים</button></td>';
                    echo '<td><button type="button">עבודות הגשה</button></td>';
                    echo '<td><button type="button"> מבחנים פתורים</button></td></tr>';
                }
            }

    ?>
  </table>

  <footer>
          <ul class="nav">
            <li> <a href="FAQ.html">שאלות ותשובות</a></li>
            <li> <a href="#">עלינו</a></li>
          </ul>
    </footer>


</body>
</html>
<?php
include('session.php');
?>

<!DOCTYPE html>
<html>
  <head>
    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <meta name="description" content="Affordable and professional web design">
	  <meta name="keywords" content="web design, affordable web design, professional web design">
  	<meta name="author" content="Brad Traversy">
    <title>TEACHY- אתר לחיפוש ושיתוף ידע</title>
    <link rel="stylesheet" href="./css/style.css">
    <link href="//netdna.bootstrapcdn.com/bootstrap/3.1.0/css/bootstrap.min.css" rel="stylesheet" id="bootstrap-css">
    <script src="//netdna.bootstrapcdn.com/bootstrap/3.1.0/js/bootstrap.min.js"></script>
    <script src="//code.jquery.com/jquery-1.11.1.min.js"></script>
    <style>
.user-row {
    margin-bottom: 14px;
}

.user-row:last-child {
    margin-bottom: 0;
}

.dropdown-user {
    margin: 13px 0;
    padding: 5px;
    height: 100%;
}

.dropdown-user:hover {
    cursor: pointer;
}

.table-user-information > tbody > tr {
    border-top: 1px solid rgb(221, 221, 221);
}

.table-user-information > tbody > tr:first-child {
    border-top: 0;
}


.table-user-information > tbody > tr > td {
    border-top: 0;
}
.toppad
{margin-top:20px;
}

	</style>
  </head>
  <body>
    <header>
      <div class="container">
        <div id="branding">
          <img src="./img/logo.png">
        </div>
        <nav>
          <ul>
           <li> <a href="">התנתק</a></li>
            <li> <a href="FAQ.html">שאלות ותשובות</a></li>
            <li> <a href="#">עלינו</a></li>
            <li class="current"> <a href="index.php">עמוד הבית</a></li>
			<li> <a href="Search1.html">חיפוש ידע</a></li>
			<li> <a href="Share1.html">שיתוף ידע</a></li>
			<li> <a href="">הפרופיל שלך</a></li>
          </ul>
        </nav>
      </div>
    </header>

<div class="container">
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6 col-xs-offset-0 col-sm-offset-0 col-md-offset-3 col-lg-offset-3 toppad" >
   
          <div class="panel panel-info">
            <div class="panel-heading" style="padding:20px">
              <h3  class="panel-title" style="float:right">הפרופיל האישי שלך</h3>
            </div>
            <div class="panel-body">
              <div class="row">
                <div class="col-md-3 col-lg-3 " align="center"> <img alt="User Pic" src="https://zionna.mtacloud.co.il/fbtest/img/<?php echo $user_picture; ?>.jpg" class="img-circle img-responsive"> </div>
                <div class=" col-md-9 col-lg-9 "> 
                  <table class="table table-user-information">
                    <tbody>
                      <tr>
                        <td><?php echo $login_session; ?></td>
                        <td>:שם משתמש</td>
                      </tr>
                      <tr>
                        <td>06/23/2013</td>
                        <td>:טלפון</td>
                      </tr>
                      <tr>
                        <td><?php echo $user_credit; ?></td>
                        <td>:קרדיט</td>
                      </tr>
                         
                       <tr>
                        <td>:סטאטוס</td>
                        <td>Female</td>
                      </tr>
                        <tr>
                        <td>:השיעורים שלי</td>
                        <td>Kathmandu,Nepal</td>
                      </tr>
                     
                    </tbody>
                  </table>
                  
                  <a href="#" class="btn btn-primary">הצג את השיעורים שלי</a>
                  <a href="#" class="btn btn-primary">Team Sales Performance</a>
                </div>
              </div>
            </div>
            
          </div>
        </div>
      </div>
    </div>
     <footer>
      <p>נוצר ע״ רעון גל וציון האלופים &copy; 2018</p>
    </footer>
  </body>
</html>


  </body>
 </html>
 
 <?php
     include('config.php');
     include('session.php');

?>

<!DOCTYPE html>
<html dir="rtl" lang="ar">
    <head>

    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
     <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Teachy| Private Teacher Search</title>
    <link rel="stylesheet" href="./css/style.css">

    <style>

      .imgStatus
      {
        float:right;
        size: 5px;
      }

    </style>


</head>

<body>
	<header>
		<div class="container">

         <div id="branding">
          <img src="./img/logo.png">
         </div>

         <div id="branding2">
          <a href="#">
            <img src="./img/p.png">
          </a> 
        </div>

          <ul class="nav">
            <li>  <a href="share.html">שיתוף ידע</a></li>
            <li class="current"> <a href="#">חיפוש ידע</a></li>
          </ul>

          <?php if ($user_status == "מתחילן") echo '<img class="imgStatus" src="./img/status/baby.png"></img>';
          elseif ($user_status == "נכנס לעניינים") echo '<img class="imgStatus" src="./img/status/student.png"></img>';
          elseif ($user_status == "בוס") echo '<img class="imgStatus" src="./img/status/boss.png"></img>';
          elseif ($user_status == "צ'יף") echo '<img class="imgStatus" src="./img/status/chief.png"></img>';
          elseif ($user_status == "רוקסטאר") echo '<img class="imgStatus" src="./img/status/rockstar.png"></img>';

?>

      </div>
    </div>
    </header>

    <form method="post" action="afterSearch.php">
      <div class="container"> 

         <table>
    <tr> 
      <th>שם המורה</th>
      <th>סטטוס</th>
      <th>טלפון</th>
     
    </tr>
    <tbody id="myTable">

        <?php
        $course_id=$_POST['add'];

      $result=mysqli_query($db,"SELECT * from users INNER JOIN Private_teachers on users.id=Private_teachers.userID AND Private_teachers.courseID=$course_id");

      if ($result->num_rows>0){ 
                while($row=$result->fetch_assoc()){
                    echo '<tr><td>'.$row['name'].'</td>';
                    echo '<td>'.$row['status'].'</td>';
                    echo '<td>'.$row['phoneNumber'].'</td></tr>';

                  }
                }
                    
              ?>
       </tbody>
       </table>
       </div>
      </form>
      
</body>
</html>

 
