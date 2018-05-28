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
<html>
<head>
    <head>
    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
	<title>TEACHY- אתר לחיפוש ושיתוף ידע</title>    
	<link rel="stylesheet" href="./css/style.css">
  <style>
 .form{
     
    background-color: #f2f2f2;
    padding: 10px;
    margin-bottom:100px;
    margin-top:80px;
    position:relative;
    margin-left:500px;
    color:black;
    font-weight:bold;
}
input[type=file]{
  margin left:70px;
}
input[type=text]{
  margin right:30px;
}
h6{
	float:right;
	margin-top: 30px;
	margin-right:150px;
}

</style>
  </head>
<body>
	<header>

      <div class="container">

       <div id="branding">
          <a href="profile.php">
          <img src="./img/logo.png">
        </a>
         </div>

         <div id="branding2">
          <a href="userProfile.php">
            <img src="./img/p.png">
          </a> 
        </div>

          <ul class="nav">
            <li> <a href="#">שיעורים פרטיים</a></li>
            <li class="current"> <a href="Share.html">שיתוף ידע</a></li>
            <li> <a href="Search.html">חיפוש ידע</a></li>
          </ul>

      </div>
    </header>
    <?php
$selected_id= $_POST['add'];
$result=mysqli_query($db,"SELECT * from courses where id='$selected_id'");
$row = mysqli_fetch_array($result,MYSQLI_ASSOC);
  $name_of_course= $row['name'];


?>
 <h6> שם הקורס: <?php echo $name_of_course; ?> </h6>
<form action="afterUpload.php" method='post' enctype="multipart/form-data" class="form">
<input name="courseName" type="hidden" value=<?php echo $name_of_course; ?> />
<input name="courseId" type="hidden" value=<?php echo $selected_id; ?>/>
<input name="user_id" type="hidden" value=<?php echo $user_id; ?> />
<p>:אנא בחר את סוג הקובץ</p>
<select required name="description_entered"> <br><br>
  <option value="">:לא נבחר ערך</option>
  <option value="עבודה">עבודה</option>
  <option value="סיכום">סיכום</option>
  <option value="סרטון הדרכה">סרטון הדרכה</option>
  <option value="מבחן פתור">מבחן פתור</option>
</select>
<div class="upload_b">
<input type="file" name="file"/><br><br>
</div>
<input type="submit" name="submit" value="העלה"/>

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
     include('session.php');
     
?>
<!DOCTYPE html>
<html dir="rtl" lang="ar">
    <head>
    <link href="https://fonts.googleapis.com/css?family=Varela+Round" rel="stylesheet">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
     <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
	<title>TEACHY- אתר לחיפוש ושיתוף ידע</title>    
	<link rel="stylesheet" href="./css/style.css">
  <style>
          .show_more {
    cursor: pointer;
    display: block;
    padding: 10px 0;
    text-align: center;
    font-weight:bold;
}
.loding {
    background-color: #e9e9e9;
    border: 1px solid;
    border-color: #c6c6c6;
    color: #333;
    font-size: 12px;
    display: block;
    text-align: center;
    padding: 10px 0;
    outline: 0;
    font-weight:bold;
}
.loding_txt {
    background-image: url(loading.gif);
    background-position: left;
    background-repeat: no-repeat;
    border: 0;
    display: inline-block;
    height: 16px;
    padding-left: 20px;
}

.img-permissions{
  width: 30%;
}

table.design {
    table-layout: fixed;
    width: 100%;    
}



@media(max-width: 768px){
.img-permissions{
    float:right;
    text-align:center;
    width:100%;

  }

.table-responsive {
    min-height: .01%;
    overflow-x: auto;
    width:55%;
}

@media screen and (max-width: 767px) {
    .table-responsive {
        width: 100%;
        margin-bottom: 15px;
        overflow-y: hidden;
        -ms-overflow-style: -ms-autohiding-scrollbar;
        border: 1px solid #ddd;
    }
    .table-responsive > .table {
        margin-bottom: 0;
    }
    .table-responsive > .table > thead > tr > th,
    .table-responsive > .table > tbody > tr > th,
    .table-responsive > .table > tfoot > tr > th,
    .table-responsive > .table > thead > tr > td,
    .table-responsive > .table > tbody > tr > td,
    .table-responsive > .table > tfoot > tr > td {
        white-space: nowrap;
    }
}
  </style>
	<script>
function check(){
 alert("<?PHP check(); ?>");
 }
 function checkStatus(){
 alert("<?PHP checkStatus(); ?>");
 }
 function phpQuery(x){
   var xhttp = new XMLHttpRequest();
    xhttp.open("POST", "update.php", true);
      xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      alert(xhttp.responseText);
      window.location.reload();
    }
  };

  xhttp.send("name="+x);
 }

</script>

<script type="text/javascript">
$(document).ready(function(){
    $(document).on('click','.show_more',function(){
        var ID = $(this).attr('id');
        var courseID= document.getElementById("request").innerHTML;
        $('.show_more').hide();
        $('.loding').show();
        $.ajax({
            type:'POST',
            url:'files_results.php',
            data: {"id": ID, "courseId": courseID},
            success:function(html){
                $('#show_more_main'+ID).remove();
                $('.postList').append(html);
            }
        });
    });
});
</script>
	
	 </head>
<body>
  <header>
   <div class="container">
         <div id="branding">
          <a href="profile.php">
          <img src="./img/logo.png">
        </a>
      </div>
         
          <ul class="nav">
            <li>  <a href="userProfile.php" style="color:#000000; text-decoration:underline">פרופיל אישי</a></li>
            <li>  <a href="Share.html">שיתוף ידע</a></li>
            <li class="current"> <a href="Search.html">חיפוש ידע</a></li>
            <li> <a href="comments.php">המלצות</a></li>
            <li> <a href="logout.php">התנתק</a></li> 
          </ul>

      </div>
    </div>
    </header>
<div class="container">
        <br>
        
      <?php
      $selected_course_id = $_POST['add'];
      $resultCourse=mysqli_query($db,"SELECT * from courses where id=$selected_course_id");
      $rowCourse=$resultCourse->fetch_assoc();
      $courseName=$rowCourse['name'];
      
      ?>
      <h3> שם הקורס: <?php echo $courseName; ?></h3>

      <h2> יתרת הקרדיט שלך היא: <?php echo $user_credit; ?></h2>

        <p id="request" style="display: none;"><?php echo $selected_course_id; ?></p>
        <div class="postList">
          <?
    		$query = "SELECT * FROM Uploaded_files WHERE courseId='$selected_course_id' AND Status='אושר' ORDER BY id DESC LIMIT 8";
    		$result=mysqli_query($db,$query);

    		if ($result->num_rows>0){ ?>
     <div class="table-responsive">     
    <table class="design">
    <tr> 
      <th> הרשאה</th>
      <th>שם הקובץ</th>
      <th>סוג הקובץ</th>
      <th>עלות</th>
      <th>פעולה</th>
    </tr>
    <?
                while($row=$result->fetch_assoc()){
                  $postID=$row['id'];
                	if ($row['descreption'] == "סרטון הדרכה" && ($user_status=='מתחילן' || $user_status=='חובבן')){
                    echo '<tr><td><img src="./img/locked.png" class="img-permissions"</img></td>';
                    echo '<td>'.$row['file'].'</td>';
                    echo '<td>'.$row['descreption'].'</td>';
                    echo '<td>'.$row['Value'].'</td>';
                    echo '<td><button class="button_5" onclick="checkStatus()">הורד</button></td></tr>';
                    }


			         else
                    { 
                      if($row['Value']>$user_credit){
                      echo '<tr><td><img src="./img/unlocked.png" class="img-permissions"</img></td>';
                     echo '<td>'.$row['file'].'</td>';
                    echo '<td>'.$row['descreption'].'</td>';
                    echo '<td>'.$row['Value'].'</td>';
                    echo '<td><button class="button_5" onclick="check()">הורד</button></td></tr>';
                  }

                  else
                    {
                    	
                      echo '<tr><td><img src="./img/unlocked.png" class="img-permissions"</img></td>';
                    	echo '<td>'.$row['file'].'</td>';
                    	echo '<td>'.$row['descreption'].'</td>';
                    	echo '<td>'.$row['Value'].'</td>';
                    	echo '<td><a style="text-decoration: none;" href="https://zionna.mtacloud.co.il/fbtest/upload/'.$row['file'].'" download><button class="button_5" onclick="phpQuery('.$row['Value'].')">הורד</button></a></td></tr>';
                    }

                    	
                    }
                    	
                 }
?>
              </table>
               <div class="show_more_main" id="show_more_main<?php echo $postID; ?>">
                <span id="<?php echo $postID; ?>" class="show_more" title="Load more posts">הצג עוד קבצים</span>
                <span class="loding" style="display: none;"><span class="loding_txt">טוען...</span></span>
                </div>
              <?     
            }
        else
          echo "אין קבצים זמינים להורדה בקורס זה";?>
      </div>

      <?

            function check()
{
echo "אין ביתרתך מספיק קרדיט להורדת הקובץ";
}
          function checkStatus(){
            echo "ההורדה נכשלה! אינך בסטאטוס המאפשר הורדת סרטון הדרכה";
          }



    ?>
            </div>
 
    <footer>
         <ul class="nav">
            <li> <a href="FAQ_after_login.html">שאלות ותשובות</a></li>
           <li> <a href="about_after_login.html">עלינו</a></li>
            <li> <a href="Prices.html">מחירון</a></li>
          </ul>
    </footer>
</body>
</html>







