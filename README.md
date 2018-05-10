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


 
