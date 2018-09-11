# Assignment Boilerplate

## Table of Contents

* [Academic Integrity and Collaboration](#academic-integrity-and-collaboration)
* [Setup and Running the App](#setup-and-running-the-app)

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

#### Post a comment
*Request:* `POST /api/post/{id}/comment/`

*Body:* 
````javascript
{
  "text": <USER INPUT>
}
````

*Response:*
````javascript
{
  "success": true,
}
````
