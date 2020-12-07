# SequelizeReverseEngineering

A README file walk-through of the code in this repository to help the user read and understand the code of this program

# Sequelize Homework - Reverse Engineering Code

## This is a walk-through explanation of the files included in this repository and helps the user understand how to read the code for this program

### server.js

Var: express, session, passort –--------require these node packages to run complete program properly
PORT –--------------- use HEROKU or local port number for server
Var:db --------------- require “models” folder
Var:app------------- express skeleton code to run properly
Require(“./routes”)-------------need to link the html and api routes for navigating program
Db.sequelize.sync()----------------------links database and console logs upon starting the program to show server is connected

### package.json

Shows log of dependencies, the required packages to run the program

### config.json

Once the user downloads this git project with all files included, they will enter their unique username and password. The database should be the name of the downloaded sql database file, or whatever the user decides to call their database if creating it on their own.

### passport.js

Password/log-in program code needed to authorize the user for using the program. Makes sure that user input email and password match what is stored in the database. If error, a message stating “incorrect” or “does not exist” will display. Otherwise if both work, then access will be granted.
module.exports----------- allows for linking this code to be called from other files in the program

### isAuthenticated.js

If the log-in data matches what is in the database, access routes to the site requested. Otherwise if incorrect credentials are entered, the user is redirected to log-in again and not granted access to the program.

### models/index.js

Var: fs,sequelize,basename,env,config,db ----------------- all required packages and files needed to run program properly
If(config.use.env_variable)-------------------listens to the database for proper user credential input
Fs.readdirSync(\_\_dirname)----------------- gets specific files and want the model to have the associated director name and file
Object.keys(db)----------------------links model with database

### models/user.js

Var: bcrypt ------------------require this package to encrypt password credentials
Var:User--------------------------code to create a user and the criteria required “String” shows letters must be used, multiple of the same strings in the database can’t be used, and this field can’t be left blank. The email entered must be verified to use this program, and the password field must also not be empty.
User.prototype.validPassword------------------- retrieves encrypted user password so it can be translated and validated in the program while maintaining security.
User.addHook--------------password is automatically “hashed”, meaning it is scrambled for security and then made available to verify authentication upon log-in.

### routes/html-routes.js

Server routes for HTML pages upon going to these specific URLS. Requires the “isAuthenticated” file, and the app.get specific files are required to route to the proper channel upon verification or failure to log-in with the matched credentials.

### routes/api-routes.js

Var:db,passport--------------require these packages to run properly.
App.post(“api/login”)-------------------------- If credentials are correct, redirect to the requested page, otherwise show an error and redirect them to the log-in screen.  
If correct credentials are input, then create the user and password.
App.get(“/logout”)-----------------redirects to logout screen
App.get(“/api/user_data”)---------------shows desired data upon authenticated log-in, otherwise shows empty data if not logged in.
Id:req.user.id -----------shows and ID number instead of password for the user for increased security.

### public/js/login.js

Links the log-in button usage and user input to the other program files so it works correctly depending on proper or incorrect credentials entered by the user. Uses jquery user input to link specific categories to appropriate api routes and links their credentials to the database to verify approval of access.

### public/js/members.js

Links the program to the proper user based on their logged in username to display their unique data.
###public/js/signup.js
The code for linking buttons and user input to meet valid criteria for creating an account with this program. Linked to other files to run properly later on given that the criteria is met. Otherwise, the user receives errors and is prompted to fix them (ex. “This username already exists, please choose another one”).

### public/login.html

This is the front-end log-in screen for a user with active credentials to input that data and access the program.

### public/members.html

This is the front-end homepage upon verifying user credentials where it displays “Welcome” followed by that unique user’s name.
###public/signup.html
This is the front-end screen for a user to create an account, or allows them to click the “log-in” button which will re-direct them to the “login.html” file to access the program.

### public/stylesheets/style.css

This is the front-end code to display the listed margin value for the user so the form has 50px of space above it on the page.
