# **HW 14 Reverse Engineering Code**

## **Server.js:**
Starts by requiring the packages that deal with creating the functions that will return the middleware functions. 

The port is assigned and the models for the database are also required.

Then an instance of the app is created and express sends functions that return middleware functions that display the json data and html pages from the public folder.

The session function is is storing the user data between each request.

Then the server.js is given access to the api and html routes by requiring them for the app.

Finally the database is synced then the server is started and once it is running a message is sent to the use that the server is running.


## **Config Folder**
The config folder contains the middleware files. These files are what controls access to the app.  

The isAuthenitcated.js file will only allow users to access certain parts of the app if they are not logged in.  

The passport.js file requires the passport and passport-local npm packages which deals with storing the user data locally. Ths file also is in charge of checking what the use inputs against what is in the database to determine whether or not to allow access to the app.

The config.json file is where the database information is stored and used to access the database with the correct username and password


## **Models Folder**
User.js is a file that creates and stores a new user. The bcrypt is a package that allows you to store people's passwords in your database in a secure way.

Index.js is a file that is automatically created when setting up the models folder with sequelize.


## **Public Folder**
This folder contains the javaScript, CSS, and HTML files for the app.  

The login.js file get the user's input, trims it, and also checks that something was entered. Then the input fields are cleared. Last the information is then sent to the api-login route with the user information to determine if access should be granted.

The members.js file gets the user information that is currently logged in and diaplays the information using members.html.

The signup.js file is the same as the login.js except sends a different request. The signup adds information to the database where as the login checks the entered information against the information in the database.

The style.css adds color and style to the app.

The html files create the layout.

## **Routes**


#### API:  
The api-routes are what controls what happens after the js files using the required models folder.

the api/login route takes the data passed from the login.js and sends it to be authenticated and then if email and password are valid they are shown the members.html.

The api/signup route takes the data from the signup.js and created a new user then send the user to the login page.

The api/logout route runs a logout method and then directs the user back to the signup.html.

The api/user_data will display the user data unless they are not a user.  



#### HTML:
The html routes are used when a user travels to a different page of the site.  

This file requires teh path package to send the file's data to the appropriate html page.

The "/" route is the main page which if a user is not logged in displays the signup.html. 

Once the user signs in they are directed to the members.html page.

When the user logs out they are taken to the signup.html.



## **Changes:**

#### Bugs:
When a user were to try and sign up with an email address that is already in use the error would display "[object Object]". This is because they were trying to set the text of the alert to an object. I applied  ```JSON.stringify``` to the response and used a different part of the err response to display the email that is already being used.


#### Future Development
There should be some restrictions or requirements on the password. As it is now, you could type a one letter password and that would qualify. 

Another thing would be to add features "forgot password" and/or "forgot email"

