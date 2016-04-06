<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
    <title>Find User ID by Social Media Frog</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <meta name="description" content="Find your Instagram user ID easily, just enter your username or get your Facebook fanpage ID entering the vanity URL.">

    <!-- Schema.org markup for Google+ -->
    <meta itemprop="name" content="Find User ID" />
    <meta itemprop="description" content="Find your Instagram user ID easily, just enter your username or get your Facebook fanpage ID entering the vanity URL." />
    <meta itemprop="image" content="http://smfrog.com/images/userid.png" />

    <!-- Twitter Card data -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:site" content="@smfrogcom">
    <meta name="twitter:title" content="Find User ID">
    <meta name="twitter:description" content="Find your Instagram user ID easily, just enter your username or get your Facebook fanpage ID entering the vanity URL.">
    <meta name="twitter:creator" content="@smfrogcom">
    <meta name="twitter:image:src" content="http://smfrog.com/images/userid.png">

    <!-- Open Graph data -->
    <meta property="og:title" content="Find User ID" />
    <meta property="og:type" content="article" />
    <meta property="og:url" content="http://userid.smfrog.com" />
    <meta property="og:image" content="http://smfrog.com/images/userid.png" />
    <meta property="og:description" content="Find your Instagram user ID easily, just enter your username or get your Facebook fanpage ID entering the vanity URL." />
    <meta property="og:site_name" content="Find User ID" />
    <!-- Social Meta Tags generated with smfrog.com -->


    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.5/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/flat-ui/2.2.2/css/flat-ui.min.css">
    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
    <script src="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>

     <!--[if lt IE 9]>
    <script type="text/javascript" src="//html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->
    <style>
    h3{
        margin: 0px;
        padding: 0px;
    }
    .center{
        float: none;
        margin: 0px auto;
    }

    nav.navbar{
        margin-bottom: 0px;
    }
    .container{
        width:98% !important;
        padding-right: 0px;
        padding-left: 0px;
    }


    @media only screen and (max-width: 720px) and (min-width: 481px) {
        .container{
            width:98% !important;
        }
        
    }

    @media only screen and (max-width: 480px) {
        .container{
            width:98% !important;
        }
        h1{
            font-size: 2em;
        }
        
        .col-xs-8, .col-xs-10 {
            width:100% !important;
            clear: both;
        }
    }
    </style>
</head>
<body>
    <div class="container">

        <nav class="navbar navbar-inverse navbar-embossed" role="navigation">
            <div class="navbar-header">
              <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#navbar-collapse-01">
                <span class="sr-only">Toggle navigation</span>
              </button>
              <a class="navbar-brand" href="/">Find User ID</a>
            </div>
         </nav>


    <div class="row">
        <div class="col-xs-8 center">
            <h1 class="demo-logo">Find User ID</h1>
            <p>Find your Instagram user ID easily, just enter your username or get your Facebook fanpage ID entering the vanity URL.</p>



            <form role="form" method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
                    <input type="text" id="igname" name="igname" class="form-control" placeholder="Instagram username" value="<?php  echo $_POST['igname']?>">

                <input type="submit" name="submit" value="Get user ID" class="btn btn-primary btn-lg"> 
            </form>

            <p>&nbsp;</p>

            <form role="form" method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
                    <input type="text" id="fbname" name="fbname" class="form-control" placeholder="Facebook fanpage" value="<?php  echo $_POST['fbname']?>">

                <input type="submit" name="submit" value="Get fanpage ID" class="btn btn-primary btn-lg"> 
            </form>

        <?php

        function getInstaID($username)
        {

            $username = strtolower($username); // sanitization
            $token = "INSTAGRAM-TOKEN";
            $url = "https://api.instagram.com/v1/users/search?q=".$username."&access_token=".$token;
            $get = file_get_contents($url);
            $json = json_decode($get);
            
            /*
            echo "<pre>";
            print_r($json->data);
            echo "</pre>";
            */

            foreach($json->data as $user)
            {
                if($user->username === $username)
                {
                return '<h3>INSTAGRAM</h3><img src="' .$user->profile_picture .'" width="70"><br> <b>User ID:</b> '. $user->id .'<br> <b>Username:</b> ' . $user->full_name;
                    
                }
            }

            return 'No user found'; // return this if nothing is found
        }


        function FetchData($json_url='',$use_curl=false){
            if($use_curl){
                $ch = curl_init();
                curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
                curl_setopt($ch, CURLOPT_URL, $json_url);
                $json_data = curl_exec($ch);
                curl_close($ch);
                return json_decode($json_data);
            }else{
                $json_data = @file_get_contents($json_url);
                if($json_data == true){
                    return json_decode($json_data);
                }else{ return null;}
            }
        }

        function getFacebookID($username){

            $app_id = 'FACEBOOK-APP-ID';
            $app_secret = 'FACEBOOK-APP-SECRET';
            $facebookUrl = 'https://graph.facebook.com/'.$username.'?access_token='.$app_id.'|'.$app_secret;
                    
            $fb_id = FetchData($facebookUrl)->id;
            return '<h3>FACEBOOK</h3><img src="//graph.facebook.com/' .$username .'/picture" width="70"><br> <b>Fanpage ID:</b> '. $fb_id.'<br> <b>Username:</b> ' . $username;

        }


        if ( isset($_POST['igname']) && !empty($_POST['igname']) ){
            $user_id = getInstaID($_POST['igname']);
        }elseif ( isset($_POST['fbname']) && !empty($_POST['fbname']) ){
            $user_id = getFacebookID($_POST['fbname']);
        }else{
            $user_id = "No user found";
        }

        ?>

        <p>&nbsp;</p>

        <?php if ( isset($_POST['submit']) ){ ?>
            <div class="jumbotron">
              <p><?php echo $user_id;?></p>
            </div>
        <?php }?>
            <p>&nbsp;</p>

         </div>
        
        </div>
    </div>

    <p>&nbsp;</p>
      <p align="center">Follow us in <a href="https://twitter.com/smfrogcom" target="_blank" class="btn-sm btn-primary">@smfrogcom</a> we will love to know about you, so don't hesitate to give us some feedback in how we can improve this tool.</p>
      <p align="center"><small>Developed with <3 in Panama</small></p>

    </div>
    <script type="text/javascript" src="//s7.addthis.com/js/300/addthis_widget.js#pubid=ra-5604d5326235f0e7" async="async"></script><script type="text/javascript">
      var addthis_config = addthis_config||{};
      addthis_config.data_track_addressbar = false;
      addthis_config.data_track_clickback = false;
    </script>
</body>
</html>
