# Teachy
Sadna
<!DOCTYPE html>
<html>
<head>
<title>Facebook Login JavaScript Example</title>
<meta charset="UTF-8">
</head>
<body>
<script>

  window.fbAsyncInit = function() {
    FB.init({
      appId      : '1973583292970708',
      cookie     : true,  // enable cookies to allow the server to access 
                          // the session
      xfbml      : true,  // parse social plugins on this page
      version    : 'v2.12' 
    });

    FB.getLoginStatus(function(response) {
      statusChangeCallback(response);
    });

  };

  
  (function(d, s, id) {
    var js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s); js.id = id;
    js.src = "https://connect.facebook.net/en_US/sdk.js";
    fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));
  
	function  statusChangeCallback(response){
	 if (response.status === 'connected') {
	 console.log('user is logged in');
	}
	else {
   console.log('user is not logged in');
  }
  }
   function checkLoginState() {
    FB.getLoginStatus(function(response) {
      statusChangeCallback(response);
    });
  }

</script>


<fb:login-button scope="public_profile,email" onlogin="checkLoginState();">
</fb:login-button>

</body>
</html>
