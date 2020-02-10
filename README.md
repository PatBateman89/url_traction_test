# Url-Short-Project

This URL shortening service using MongoDB, Express, React, and Node (MERN STACK).

## Installation

```bash
npm install
npm install --prefix client
```

## Setup nodemon.json file in root directory

touch nodemon.json

```python
{

"env": {

"mongoURI": "YOUR MONGO_URI GOES HERE",

"baseUrl": "http://localhost:5000",

"NODE_ENV": "development"

}

}

```

## Usage

```python

# Run the client & server with concurrently
$ npm run dev

# Run the Express server only
$ npm run server

# Run the React client only
$ npm run client

# Server runs on http://localhost:5000 and client on http://localhost:3000

```

## My approach

First I decided I would use a traditional MERN stack and use MongoDB as my database to hold the urls entered by the client.

I immediately set up my index.js file and used it to connect to my mongoDB using mongoose.  I decided to set up my DB in the index.js file because the project was so small I felt it was appropriate to not separate the two.  

From there I setup my one model which was the urlSchema.  It only had four fields, all of which were strings.

Next I created a separate folder for my routes using Express.  At this point I imported and installed a module called valid-url to ensure that all urls entered by the client would be valid.  

I only used two routes, a simple get and post request.  The post would check if my "longUrl" was valid, and then generate a "shortUrl", after these two tasks completed without error it would save to my DB.

Afterwards I setup my get request in my index.js file inside my routes folder.  This would search for a specific urlCode and if found redirect the user client to the specified url.

Instead of testing this using postman or something similar I used a visual studio code extension called rest client, making a simple test post request.  I've kept it in the project for those who would like to test this themselves without setting up the entire frontend.

Once the backend was complete I began to work on the frontend of the project using React.

First of business was creating my state.  This would hold my shortUrl, and LongUrl, as well as multiple booleans in order to more easily toggle certain actions.

In order to make requests from the frontend/client side of the project I installed axios and created a handleSubmit() function to post the longUrl to the DB which it receives from the inputForm, while setting the state of the shortUrl. After handleSubmit is successful output() will get the shortUrl and present it to the client.  
