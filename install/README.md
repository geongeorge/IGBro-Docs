# Installation

The game is divided into 2 parts:
> - **Admin Panel** : `where the quizzes are made`
> - **Front end** : `which is uploaded to facebook`

In order to install the game we'll first install the admin panel.

## Admin panel


### Prerequisites ❓
-	Domain or subdomain should have ssl (https)
-	It is better to install in a subdomain or sub directory like quiz.mywebsite.com or mywebsite.com/quiz

### Server ⚙️
-	Make sure your server has apache or hybrid(apache+nginx)
-	Make a database (store the db_name, username, pwd temporarily)
-	Use phpmyadmin  to login with the database credentials and import yolo_new.sql

### Hosting the Files 📁 

Make sure if you’re using linux or mac you have hidden files shown. So as to show .htaccess otherwise you’ll miss it when zipping

-	Zip the files together. Don’t include database.sql (for security)
-	Upload the zip file to your server and expand it there
-	Expand(extract) it there in your server. 
-	Delete the zip file from the server(If you don’t wanna he hacked)
-	Now open these files in an editor
    -	`application/config/config.php`
        ```php
        $config['base_url'] = 'https://quiz.mywebsite.com/';

        ```
        -	Find the property **baseUrl** and change it (include the ending forward slash- / ). Use the same baseUrl you added here to add a game into user account/ products for the licensing to work.
        -	**https** is a must for intant games to work with Facebook

    -	`application/config/constants.php`
            ```php
            //custom
            define('SITE_NAME', 'Yolo');
            define('SITE_DESC', 'Fun Quizzes');
            define('GAME_ID', '1');
            define('GAME_LICENSE', '9778-2988-E3EE-XY76');
            ```
        -	Scroll down and edit the site name
        -	Add License Code from user accounts section/products in IGBro website. 
        -	After you add a game in the IGBro admin panel, you'll get a game ID. add that here. Note Game ID is **not** the same as serial number(SL.no)

    -	`application/config/database.php`
        ```php
        'hostname' => 'localhost',
        'username' => 'user',
        'password' => 'pass',
        'database' => 'yolo_db',
        ```
        -	edit database,username,password from previously saved data
-	Give the folders app_imgs and uploads full permissions (777)
-	Now visit your site https://quiz.mywebsite.com/ 
-	You’ll be redirected to login page.
-	Use the credentials to login  :
    -	`admin`
    -	`password`



## Front end

Installing IGBro front is very straight forward. Everything that the user is required to edit is moved into the `/data` folder.

- Extract the front end zip file
- 