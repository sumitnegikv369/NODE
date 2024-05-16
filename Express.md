# Definition
Express is the most popular minimalistic framework. It is built upon the built-in module HTTP of NodeJS to facilitate the simple and easy interaction between frontend and backend logic through API, and also it enables us to organize our business logic in so much pretty manner. It is much flexible and we can use it for both the web and android. Also, it provides a very simple error handling procedure.

```js
const express = require('express'); 

const app = express(); 
const PORT = 3000;

app.get('/', (req, res)=>{ 
    res.status(200); 
    res.send("Welcome to root URL of Server"); 
});

app.get('/hello', (req, res)=>{ 
    res.set('Content-Type', 'text/html'); 
    res.status(200).send("<h1>Hello GFG Learner!</h1>"); 
});

app.listen(PORT, (error) =>{ 
	if(!error) 
		console.log("Server is Successfully Running, 
				and App is listening on port "+ PORT) 
	else
		console.log("Error occurred, server can't start", error); 
	} 
); 
```

Express provides us a middleware express.static(), it accepts two arguments first one is the absolute root path of the directory whose files we are going to serve. 
We can simply use it to serve static files, by providing to app.use().
`app.use(path, express.static(root, [options]));`

Sending a single file on a route with the sendFile() function.
This function accepts an absolute URL of the file and whenever the route path is being accessed the server provides the file as an HTTP response. This process can be thought of as a single endpoint of the express.static(). It can be useful when we have to do some kind of processing before sending the file.

## Router
The express.Router() function is used to create a new router object. This function is used when you want to create a new router object in your program to handle requests. Multiple requests can be easily differentiated with the help of the Router() function in Express.js.This is the advantage of the use of the Router.

