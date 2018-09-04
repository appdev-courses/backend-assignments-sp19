# Assignment Boilerplate

## Table of Contents

* [Academic Integrity and Collaboration](#academic-integrity-and-collaboration)
* [Setup and Running the App](#setup-and-running-the-app)
* [Expected Functionality](#expected-functionality)

## Academic Integrity and Collaboration

Note that these projects should be completed **individually**. As a result, all University-standard AI guidelines should be followed.

## Setup and Running the App

#### Setup:
```sh
cd src # change directory 
virtualenv -p python3.6 venv # create a virtual environment
source venv/bin/activate # enter the virtual environment
pip install -r requirements.txt # install the required packages
```

#### Running the App:
```sh
source venv/bin/activate # enter the virtual environment
sh run.sh # start running the app
```

## Expected Functionality

#### Get all posts
*Request:* `GET /api/posts/`

*Response:*
````javascript
[
  {
    "id": 1,
    "score": "0",
    "text": "My First Post!",
    "username": "Young",
  },
  {
    "id": 2,
    "score": "0",
    "text": "My Second Post!",
    "username": "Young",
  }
]
````

#### Create a post
*Request:* `POST /api/posts/`

*Body:* 
````javascript
{
  "text": <USER INPUT>,
  "username": <USER INPUT>,
}
````

*Response:*
````javascript
{
  "id": 1,
  "text": <USER INPUT FOR TEXT>,
  "username": <USER INPUT FOR USERNAME>,
}
````

#### Get a specific post
*Request:* `GET /api/post/{id}/`

*Response:*
````javascript
{
  "id": [the url arg for id],
  "text": "Hello World!",
  "username": "Young",
}
````

#### Post a comment / Edit a post
*Request:* `POST /api/post/{id}/`

*Body:* 
````javascript
{
  "type": "comment", // can be either 'comment' or 'edit'
  "text": <USER INPUT>
}
````

*Response:*
````javascript
{
  "success": true,
}
````

#### Delete a specific post
*Request:* `DELETE /api/post/{id}/`

*Response:*
````javascript
{
  "success": true,
}
````

#### Get comments for a specific post
*Request:* `GET /api/post/{id}/comments/`

*Response:*
````javascript
[
  {
    "id": 1,
    "score": 0,
    "text": "My First Comment!",
    "username": "Young",
  }
]
````
