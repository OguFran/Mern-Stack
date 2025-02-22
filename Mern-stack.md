## MERN Stack Project 3

#### MERN Stands for:
#### - MongoDB: A NoSQL database that stores data in a flexible, document-like format (JSON-like). 
#### - Express.js: A web application framework for Node.js. It simplifies the creation of APIs (Application Programming Interfaces) and handles routing (how your app responds to different URLs).
#### - ReactJS: A JavaScript library for building user interfaces (the parts of the website users interact with). React is component-based, making it efficient for creating dynamic and interactive UIs.
#### - Node.js: A JavaScript runtime environment that allows you to run JavaScript on the server-side. Node.js is known for its speed and ability to handle many connections.

#### In this project I would be implementing a web solution based on MERN stack in AWS Cloud.

### STEP 1 - Backend Creation

#### I started by updating Ubuntu with two commands ``sudo apt update`` and ``sudo apt update -y``
![alt text](<Screenshot 2025-02-08 170931.png>)

#### After this, I inputed a command that got the location of Node.js software from Ubuntu repositories
![alt text](<Screenshot 2025-02-08 171407.png>)

The next thing I did was to install Node.js and npm
![alt text](<Screenshot 2025-02-08 171525.png>)

I then verified both installations with ``node -v`` and ``npm -v``

![alt text](<Screenshot 2025-02-08 171640.png>)

### Moving to the Application Code Setup.

#### I created a new directory for my To-Do project. Then I verified that the ``Mern-Todo`` directory is created.

![alt text](<Screenshot 2025-02-08 171735.png>)

I then changed the current directory into the newly created one and initialised the project with the ``npm init`` command. This created a new file named ``package.json``.

![alt text](<Screenshot 2025-02-08 172255.png>)

I then Installed ExpressJs which is a framework for Node.js

![alt text](<Screenshot 2025-02-08 174140.png>)

I then installed a file  ``index.js`` and confirmed it was successfully created. I also installed dotenv module.

![alt text](<Screenshot 2025-02-08 174323.png>)

I then opened the index.js file and pasted a command specifying to use port 5000 which was to be required later.
I later started the server to see if it worked. I opened the terminal in the same directory and saw the server running on port 5000 in the terminal. 

![alt text](<Screenshot 2025-02-08 205032.png>)

I ensured I created an inbound rule to open TCP port 5000 in EC2 ssecurity group.

![alt text](<Screenshot 2025-02-10 210100.png>).

### Routes
#### Our To-Do application needed to be able to 
- Create a new task
- Display list of all task
- Delete a completed task

These tasks will each be associated with some particular endpoint and will use different standard HTTP request method: POST, GET, DELETE.

I then created a __routes__ folder. Changed directory into the new folder and created a ``api.js`` file. I also copied and pasted a code inside the ``api.js`` file and this provided a placeholder routes for GET, POST, and DELETE.

![alt text](<Screenshot 2025-02-10 212116.png>)

### The next step is to create Model and a schema since the app is going to make use of Mongodb which is a NoSQL database.

To creat a shema and a model, I installed mongoose which is a Node.js package that makes working with mongodb easier. 

![alt text](<Screenshot 2025-02-10 213603.png>)

I then created a Models folder and changed directory into the newly created folder. Inside the newly created folder, I created a file and named it ``todo.js``.
Then I pasted a code inside the file created with ``vim todo.js``.

![alt text](<Screenshot 2025-02-10 213726.png>)

##### After this, I created an account and connected to the MongoDB database. 
In the ``index.js`` file, I specified ``process.env`` to access environment variables and since I had not created this file, that was the next step. After which I added the connectin stricg to access the database in it.

I needed to update the index.js to reflect the use of .env so that Node.js can connect to the database.

I then deleted existing content in the file, and updated it with a given code.

After this, I started my server using the ``node index.js`` command and got this response.

![alt text](<Screenshot 2025-02-12 182436.png>)

#### The next step was to test the backend code without Frontend using RESTful API. 

After seeing the reading about Postman, I installed it. I then created a POST request to the API ``http://<PublicIP-or-PublicDNS>:5000/api/todos`` and inputed a sample POST value. This gabbve me this result below;

![alt text](<Screenshot 2025-02-18 223017.png>)

I then created a GET request to my API ``http://<PublicIP-or-PublicDNS>:5000/api/todos``. This request was to retrieve all existing records from the To-do APPLICATION (back end requests these records from the database and sends it to us back as a response to GET request).

![alt text](<Screenshot 2025-02-18 223202.png>)

I also figured out how to send a Delete request to delete a task from the To-Do list.

![alt text](<Screenshot 2025-02-18 225133.png>)

### Step 2 - Frontend Creation

#### Since I haD completed the backend and API, it was time to create a new user interface for a Web client(browser) to interact with the application via API. To start out the front end of the To-Do app, I used the ``create-react-app`` command to scaffold the app.

After this, I had to install some dependencies - ``Concurrently`` and ``Nodemon``. Concurrenly is used to run more than one command simultaneously from the same terminal window while Nodemon is used to run and monitor the server and restarts automatically to load new changes once available. 

![alt text](<Screenshot 2025-02-18 230658.png>)

In the ``Mern-Todo`` folder, I opened the ``package.json`` file. Changed the scripts code with a new code.

#### The next step was to configure Proxy in ``package.json``. The purpose was to make it possible to access the application directly from the browser by simply calling the server url ``http://localhost:5000``.

![alt text](<Screenshot 2025-02-19 011642.png>)

Next, inside the ``Mern-Todo`` directory I ran this code ``npm run dev``.

![alt text](<Screenshot 2025-02-19 012352.png>)

I then opened the app and ran it on ``localhost:3000`` and got this result. I also opened TCP port 3000 on EC2 to gain access.

![alt text](<Screenshot 2025-02-19 011950.png>)

#### Next I created the React components. One stateless and two stateful components. 

![
](<Screenshot 2025-02-19 012753.png>)

After series of commands I ran to ensure the To-Do app was functional, I tested it on the web and got this result.

![alt text](<Screenshot 2025-02-19 013416.png>)

I had created a simple To-Do and deployed it to MERN stack. I wrote a frontend application using React.js that communicated with a backend application using Expressjs. I also created a Mongodb backend for storing tasks in a database.