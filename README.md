# Node Task Manager RESTFul API
Backend RESTful API to a task manager application

### Built With

- [Node.js](https://nodejs.org/en/)

https://task-manager-node-rest-api.herokuapp.com/

## Table of Contents

**Observation: This application is deployed in Heroku. So if you want to use it from Heroku you can skip to the REST API part where you will find all the informations you need to use the API endpoints.**

- [Setup (Optional)](#setup)
  - [Prerequisites](#prerequisites)
  - [Installing](#installing)
  - [Running the tests](#running-the-tests)
  - [Running the API](#running-the-api)
- [Authors](#authors)
  

## Setup

### Prerequisites

```
Node
Mongodb
```

### Installing

Clone the project:
```
$ git clone https://github.com/Lukazovic/node-task-manager-api.git
```

Go into the project root folder:
```
$ cd node-task-manager-api
```

Install the projects modules:
```
$ npm install
```

**Observation: You will need to setup some environment configs in order to start the server or run the tests.**

First create a config folder at the root of the project:
```
$ mkdir config
```

**To setup the server environment**: You will have to create a file at ``./config`` called ``dev.env`` and configure as the example bellow:
```
PORT=<Port-Number>
SENDGRID_API_KEY=<Sendgrid-Api-Key>
MONGODB_URL=mongodb://127.0.0.1:27017/<Data-Base-Name>
JWT_SECRET=<Secret-JWT>
```
  - **Port-Number:** A port number to acess the server ``(example: PORT=3000)``;
  - **Sendgrid-Api-Key:** A key provided by [SendGrid](https://sendgrid.com/) so you can send emails directly from the application;
  - **Data-Base-Name:** A name to the database ``(example: node-task-manager-api)``;
  - **Secret-JWT:** A secret word to generate the tokens for the API ``(example: mysecretword)``.

**To setup the tests environment**: You will have to create a file at ``./config`` called ``test.env`` and configure as the example above **EXCEPT the Data-Base-Name where you should change the name ``(example: node-task-manager-test-api)``;**

### Running the Tests
```
$ npm run test
```

## Running the API

To run the API (in the project folder):
```
$ npm run start
```

> Access in: localhost:**Port-Number**



# REST API

## All API user endpoints:

- POST: `/users` - Create new user
- POST: `/users/login` - Login a user
- PATCH: `/users/me` - Update user's informations
- GET : `/users/me` - Get a profile from a logged user
- GET: `/users/<id>` - Get a user's profile by ID
- POST: `/users/me/avatar` - Upload a logged user's avatar
- GET: `/users/me/avatar` - Get the avatar from a logged user
- GET: `/users/<id>/avatar` - Get the user's avatar profile by ID
- POST: `/users/logout` - Logout a user
- POST: `/users/logoutAll` - Logout a user from all sessions
- DELETE: `/users/me/avatar` - Delete a logged user's avatar
- DELETE: `/users/me` - Delete a logged user

## Authors

- [**Lucas Vieira**](https://github.com/Lukazovic)
