<?php
include('config.php');
session_start();
require_once __DIR__ . '/src/Facebook/autoload.php'; 

if ($db->connect_error){
  die('error: ' .$db->connect_error);
}
$fb = new Facebook\Facebook([
  'app_id' => '1973583292970708',
  'app_secret' => 'b7b4f731fa9b451fbc9fa62c8058980a',
  'default_graph_version' => 'v2.12',
  ]);
$helper = $fb->getRedirectLoginHelper();
$permissions = ['email']; 
  
try {
  if (isset($_SESSION['facebook_access_token'])) {
    $accessToken = $_SESSION['facebook_access_token'];
  } else {
      $accessToken = $helper->getAccessToken();
  }
} catch(Facebook\Exceptions\FacebookResponseException $e) {
  // When Graph returns an error
  echo 'Graph returned an error: ' . $e->getMessage();
    exit;
} catch(Facebook\Exceptions\FacebookSDKException $e) {
  // When validation fails or other local issues
  echo 'Facebook SDK returned an error: ' . $e->getMessage();
    exit;
 }
if (isset($accessToken)) {
  if (isset($_SESSION['facebook_access_token'])) {
    $fb->setDefaultAccessToken($_SESSION['facebook_access_token']);
  } else {
    // getting short-lived access token
    $_SESSION['facebook_access_token'] = (string) $accessToken;
      // OAuth 2.0 client handler
    $oAuth2Client = $fb->getOAuth2Client();
    // Exchanges a short-lived access token for a long-lived one
    $longLivedAccessToken = $oAuth2Client->getLongLivedAccessToken($_SESSION['facebook_access_token']);
    $_SESSION['facebook_access_token'] = (string) $longLivedAccessToken;
    // setting default access token to be used in script
    $fb->setDefaultAccessToken($_SESSION['facebook_access_token']);
  }
  // redirect the user back to the same page if it has "code" GET variable
  if (isset($_GET['code'])) {
    header('Location: ./');
  }
  // getting basic info about user
  try {
    $profile_request = $fb->get('/me?fields=name,first_name,last_name,email');
    $profile = $profile_request->getGraphNode()->asArray();
  } catch(Facebook\Exceptions\FacebookResponseException $e) {
    // When Graph returns an error
    echo 'Graph returned an error: ' . $e->getMessage();
    session_destroy();
    // redirecting user back to app login page
    header("Location: ./");
    exit;
  } catch(Facebook\Exceptions\FacebookSDKException $e) {
    // When validation fails or other local issues
    echo 'Facebook SDK returned an error: ' . $e->getMessage();
    exit;
  }
  $name=$profile['name'];
  $id=$profile['id'];
  $first_name=$profile['first_name'];
  $temp="SELECT id FROM users WHERE id='$id'";
  $checkResult=mysqli_query($db,$temp);
  if (mysqli_num_rows($checkResult)>0){
    $_SESSION['login_user'] = $name;
         header("location: profile.php");
  }
  else{
   $sql = "INSERT INTO users(id,name,token)
  VALUES ('{$id}', '{$name}', '{$accessToken}')";
  if ($db->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $db->error;
}
}

$db->close();
} else {
  $loginUrl = $helper->getLoginUrl('https://zionna.mtacloud.co.il/fbtest/login.php', $permissions);
  echo '<a href="' . $loginUrl . '">Log in with Facebook!</a>';

}


 
