# Node Task Manager RESTFul API
Backend RESTful API to a task manager application

### Built With

- [Node.js](https://nodejs.org/en/)
- [mongoDB](https://www.mongodb.com/)

https://task-manager-node-rest-api.herokuapp.com/

## Table of Contents

**Observation: This application is deployed in Heroku. So if you want to use it from Heroku you can skip the setup part.**

- [Setup (Optional)](#setup)
  - [Prerequisites](#prerequisites)
  - [Installing](#installing)
  - [Running the tests](#running-the-tests)
  - [Running the API](#running-the-api)
- [All Endpoints](#all-endpoints)
  - [Users Endpoints](#users-endpoints)
  - [Tasks Endpoints](#tasks-endpoints)
- [All Paramethers](#all-paramethers)
  - [Users Paramethers](#users-paramethers)
  - [Tasks Paramethers](#tasks-paramethers)
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

### Running the API

To run the API (in the project folder):
```
$ npm run start
```

> Access in: localhost:**Port-Number**

## All Endpoints

### Users Endpoints:

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

### Tasks Endpoints:

- POST: `/tasks` - Create new task to a logged user
- GET: `/users` - Get all tasks from a logged user
- GET : `/tasks/<id>` - Get a task by ID from a logged user
- PATCH: `/tasks/<id>` - Update a task by ID from a logged user
- DELETE: `/tasks/<id>` - Delete a task by ID from a logged user

## All Paramethers

### Users Paramethers

|   Paramether   |       Description   |   Type     |
| :------------: | :-----------------: | :--------: |
|      _id       |   User's ID         |   String   |
|      name      |   User's name       |   String   |
|      age       |   User's age        |   Integer  |
|      email     |   User's email      |   String   |
|    password    |   User's password   |   String   |

> **Observation: password length has to be greater than 7 and can not contain the word `password`**

### Tasks Paramethers

|   Paramether   |      Description       |   Type     |
| :------------: | :--------------------: | :--------: |
|      _id       |    Task's ID           |   String   |
|   description  |    Tak's description   |   String   |
|   completed    |    Task's situation    |   Boolean  |

## How to use users API Endpoints

### Create new user

#### Method:

- POST: `/users`

#### URL Example

> [https://task-manager-node-rest-api.herokuapp.com/users](https://task-manager-node-rest-api.herokuapp.com/users)

#### Paramethers

|   Paramether   |       Description    |     Type     |   Required   |
| :------------: | :------------------: | :----------: | :----------: |
|      _id       |   User's ID          |    String    |     False    |
|      name      |   User's name        |    String    |     True     |
|      age       |   User's age         |    Integer   |     False    |
|      email     |   User's email       |    String    |     True     |
|    password    |   User's password    |    String    |     True     |
|  Authorization | Session user's Token | Bearer Token |     True     |

##### JSON example:

```json
{
	"name": "User Test",
	"age": 18,
	"email": "test@email.com",
	"password": "idontknow"
}
```

##### Observation:

> **As response you will receive a token so you will be able to use it to authenticate the user when it needed**

##### Response example:

```json
{
    "user": {
        "age": 18,
        "_id": "5e6e0117bb997d0017c94f0d",
        "name": "User Test",
        "email": "test@email.com",
        "createdAt": "2020-03-15T10:19:03.027Z",
        "updatedAt": "2020-03-15T10:19:03.076Z"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTZlMDExN2JiOTk3ZDAwMTdjOTRmMGQiLCJpYXQiOjE1ODQyNjc1NDN9.aAvvkMcEaSeQxKyu6wDQXfQ1z4hM9zn1myJT8Iw689U"
}
```

## Authors

- [**Lucas Vieira**](https://github.com/Lukazovic)
