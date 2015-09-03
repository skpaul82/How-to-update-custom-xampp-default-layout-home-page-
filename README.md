# How-to-update-custom-xampp-default-layout-home-page-
Update (/custom) xampp default layout/ home page

We are building website and applications on localhost and I use XAMPP for my local development.

After installing Xampp, we always get a default home page from Xampp and most of the time we don’t need that. Basically before writing this article I always delete all items of htdocs folder, but sometimes we need to know things like versions and if functions are enable or not and also the limits various variables. So by using the below script you can easily get a good view of your localhost projects and as well as databases from phpmyadmin.

 

 

In the header put this css code into the style tag for a better view

 

body {

background: #fcfcfc;

color: #111;

font-family: verdana, sans-serif;

padding: 0;

margin: 0;

}

#main {

width: 100%;

position: relative;

}

.container {

padding: 1em;

}

#menu { float: left; width: 24%;  }

#menu ul { padding: 0; border-right: 3px solid white; margin: 0; }

ul li { list-style-type: none; }

ul li a {

display: block;

background: #eee;

padding: 4px 7px;

border-top: 2px solid #fff;

}

ul li a:hover {

background: #B6C6D7;

color: black;

}

iframe {

border: 0 none;

overflow: hidden;

width: 74%;

height: 95%;

padding-left: 1%;

}

.clear-block {

width: 100%;

height: 1px;

clear: both;

}

Add this css file for a look like phpmyadmin

<link rel="stylesheet" type="text/css" href="phpmyadmin/phpmyadmin.css.php"></script>

 

Put this code into the body

<div id="main">

<div class="container">

<div id="menu">

<a href="/xampp"><strong>XAMPP for Windows</strong></a>

<hr>

<p><strong>/htdocs (Websites)</strong></p>

<ul>

<?php

$www = $_SERVER['DOCUMENT_ROOT'];

$files = scandir($www);

usort($files, 'strcasecmp');

foreach($files as $key => $value){

if($value[0] != '.' && is_dir($value))

echo '<li><a href="/' . $value . '">' . $value . '</a></li>';

}

?>

</ul>

</div>

<div>

<iframe src="http://localhost/phpmyadmin/"></iframe>

</div>

<div class="clear-block"></div>

</div>

</div>

Now you are done. And save this file as index.php at htdocs

 

Or you can download the file from here
