# Assignment Boilerplate

## Table of Contents

* [Academic Integrity and Collaboration](#academic-integrity-and-collaboration)
* [Expected Functionality](#expected-functionality)

## Academic Integrity and Collaboration

Note that these projects should be completed **individually**. As a result, all University-standard AI guidelines should be followed.

## Expected Functionality

#### Get all posts
*Request:* `GET /api/posts`

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
*Request:* `POST /api/posts`

*Body:* 
````javascript
{
  "text": "[user input]",
  "username": "[user input]",
}
````

*Response:*
````javascript
{
  "id": 1,
  "text": "[the user input for text]",
  "username": "[the user input for username]",
}
````

#### Get a specific post
*Request:* `GET /api/post/{id}`

*Response:*
````javascript
{
  "id": [the url arg for id],
  "text": "Hello World!",
  "username": "Young",
}
````

#### Post a comment / Edit a post
*Request:* `POST /api/post/{id}`

*Body:* 
````javascript
{
  "type": "comment", // can be either 'comment' or 'edit'
  "text": "[user input]"
}
````

*Response:*
````javascript
{
  "success": true,
}
````

#### Delete a specific post
*Request:* `DELETE /api/post/{id}`

*Response:*
````javascript
{
  "success": true,
}
````

#### Get comments for a specific post
*Request:* `GET /api/post/{id}/comments`

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
