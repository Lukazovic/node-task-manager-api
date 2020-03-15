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
	"_id": "5e57032553882237985596f1",
 	"name": "Eleanor Decker",
	"age": 18,
	"gender": "M",
	"location": {
		"latitude": 90,
		"longitude": 180
	},
	"inventory": {
		"quantityFijiWater": 15,
		"quantityCampbellSoup": 15,
		"quantityFirstAidPouch": 15,
		"quantityAk47": 15
	},
	"situation": {
		"quantityFlags": 0
	}
}
```

##### Observations:

> It's forbidden to register zombies!

> It is not required to inform the user ID and if you don't the ID will be auto generated.
---

## List all survivors

#### Method:

- GET: `/api/survivors`

#### URL Example:

> [http://localhost:3001/api/survivors](http://localhost:3001/api/survivors)

---

## Get survivor

#### Method

- GET: `/api/survivors/<id>`
  - `<id> is the identifier of the survivor.`

#### URL Example:

> [http://localhost:3001/api/survivors/5e57032553882237985596f1](http://localhost:3001/api/survivors/5e57032553882237985596f1)

---

## Update survivor location

#### Method

- PATCH: `/api/survivors/location/<id>`
  - `<id> is the identifier of the survivor.`

#### URL example:

> [http://localhost:3001/api/survivors/location/5e57032553882237985596f1](http://localhost:3001/api/survivors/location/5e57032553882237985596f1)

#### Paramethers

| Paramether |      Description       |     Type      |
| :--------: | :--------------------: | :-----------: |
|  latitude  |   Updated latitude     |    Decimal    |
| longitude  |   Updated longitude    |    Decimal    |

JSON example:

```json
{
	"latitude": 0,
	"longitude": 0
}
```

---

### Flag survivor as infected

#### Method

- PUT: `/api/survivors/contamination`

#### URL example:

> [http://localhost:3001/api/survivors/contamination](http://localhost:3001/api/survivors/contamination)

#### Paramethers

| Paramether |       Description       |    Type     |
| :--------: | :---------------------: | :---------: |
|    id      |  Survivor ID to report  |   Decimal   |

JSON example:

```json
{
	"_id": "5e57032553882237985596f1"
}
```

##### Observations:

> Survivor will have **"infected": true** in **GET** when **quantityFlags >= 5**.

### Trade items between non infected survivors

#### Method

- PUT: `/api/survivors/<id>/transactional/<idTarget>`
  - `<id> is the identifier of the survivor who wants to trade`
  - `<idTarget> is the identifier of the survivor who survivor wants to trade with`

#### URL example:

> [http://localhost:3001/api/survivors/5e57032553882237985596f1/transactional/5e57032553882237985596f3](http://localhost:3001/api/survivors/5e57032553882237985596f1/transactional/5e57032553882237985596f3)

#### Paramethers


|       Paramether      |                 Description                        |                 Type                  |
| :-------------------: | :------------------------------------------------: | :-----------------------------------: |
|          id           |                Survivor ID                         |                String                 |
|       idTarget        |                Survivor ID                         |                String                 |
|    quantityFijiWater  |        How many Fiji Waters the survivor has       |                Integer                |
|  quantityCampbellSoup |       How many Campbell Soup the survivor has      |                Integer                |
| quantityFirstAidPouch |      How many First Aid Pouch the survivor has     |                Integer                |
|      quantityAk47     |           How many AK-47 the survivor has          |                Integer                |

JSON example:

```json
[
	{
		    "quantityFijiWater": 1,
		    "quantityCampbellSoup": 1,
		    "quantityFirstAidPouch": 1,
		    "quantityAk47": 1
	},
	{
		    "quantityFijiWater": 1,
		    "quantityCampbellSoup": 1,
		    "quantityFirstAidPouch": 1,
		    "quantityAk47": 1
	}
]
```

Observations:

> In order to complete the transaction both sides of the trade must offer the same amount of points.
> So it must respect the price table below, where the value of an item is described in terms of points.

> Survivors are not allowed to trade all their Fiji Water or First Aid Pouch since they would die without water for a day or if  if they have a severe untreated wound.


|       Item        |   Points  |
| :---------------: | :-------: |
| 1 Fiji Water      | 14 points |
| 1 Campbell Soup   | 12 points |
| 1 First Aid Pouch | 10 points |
| 1 AK-47           | 8 points  |

### Get reports

#### Method

- GET: `/api/reports`

#### URL example:

> [http://localhost:3001/api/reports](http://localhost:3001/api/reports)

##### Observations:

> The API will offer the following reports:
>
> 1.  Percentage of infected survivors;
> 2.  Percentage of non-infected survivors;
> 3.  The average amount of each kind of resource by the survivor (e.g. 10 Fiji Waters per survivor);
> 4.  Points lost because of an infected survivor.

## Authors

- [**Lucas Vieira**](https://github.com/Lukazovic)
