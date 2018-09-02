# Assignment Boilerplate

## Table of Contents

* [Academic Integrity and Collaboration](#academic-integrity-and-collaboration)
* [Expected Functionality](#expected-functionality)

## Academic Integrity and Collaboration

Note that these projects should be completed **individually**. As a result, all University-standard AI guidelines should be followed.

## Expected Functionality

#### Create a Board
*Request:* `POST /kanban/boards?title={board_title}`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "board": {
      "board_elements": [],
      "created_at": "2017-05-15T22:43:32+00:00",
      "id": 1,
      "title": "My Awesome Board",
      "updated_at": "2017-05-15T22:43:32+00:00"
    }
  }
}
````

#### Delete a Board
*Request:* `DELETE /kanban/boards?id={board_id}`

*Response:*
````javascript
{
  "success": true
}
````

#### Get Boards
*Request:* `GET /kanban/boards`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "boards": [
      {
        "created_at": "2017-05-15T22:43:32+00:00",
        "id": 1,
        "title": "My Awesome Board",
        "updated_at": "2017-05-15T22:43:32+00:00",
        "todo_count": 1,
        "inprogress_count": 3,
        "done_count": 5
      },
      // More boards ..
    ]
  }
}
````

#### Get Board By ID
*Request:* `GET /kanban/boards/{board_id}`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "board": {
      "id": 1,
      "title": "My Awesome Board",
      "created_at": "2017-05-15T22:43:32+00:00",
      "updated_at": "2017-05-15T22:43:32+00:00",
      "todo": [
        // todo board_elements, see structure below
      ],
      "inprogress": [
        // inprogress board_elements, see structure below
      ],
      "done": [
        // done board_elements, see structure below
      ]
    }
  }
}
````

#### Create a Board Element
*Request:* `POST /kanban/board_elements?board_id={board_id}&description={description}&category={todo|inprogress|done}`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "board_element": {
      "id": 1,
      "board_id": 2,
      "category": "todo",
      "created_at": "2017-05-15T22:43:32+00:00",
      "updated_at": "2017-05-15T22:43:32+00:00",
      "description": "A Todo Task, I should get this done!",
      "tags": [
        // optional part of the assignment, but an empty array should be returned regardless
      ]
    }
  }
}
````

#### Delete a Board Element
*Request:* `DELETE /kanban/board_elements?board_element_id={element_id}`

*Response:*
````javascript
{
  "success": true
}
````

#### Advance a Board Element
A.k.a. make a `todo` board element an `inprogress` board element, or an `inprogress`
board element a `done` board element.

*Request:* `POST /kanban/board_elements/advance?id={board_element_id}`

*Response:*
````javascript
{
  "success": true
}
````

## Extensions

### 1. Tags
As you might notice, the front-end features an "+ Add Tag" button on every board element.  
A tag can belong to several different board elements, and a board element can have many tags.
If you wish to make the tags portion of your Kanban board work, you can fulfill the below
spec and then run several POST requests to the following URL to fill your database with
tags to be added to board elements (I use `httpie` in my examples):

````bash
http post localhost:5000/kanban/tags?name=exercise
http post localhost:5000/kanban/tags?name=school
http post localhost:5000/kanban/tags?name=video+games
....
````
The spec is as follows:

#### Create a Tag
*Request:* `POST /kanban/tags?name={name}`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "tag": {
      "board_elements": [],
      "created_at": "2017-05-15T22:50:28+00:00",
      "id": 4,
      "name": "exercise",
      "updated_at": "2017-05-15T22:50:28+00:00"
    }
  }
}
````

#### Get All Tags
*Request:* `GET /kanban/tags`

*Response:*
````javascript
{
  "success": true,
  "data": {
    "tags": [
      {
        "board_elements": [],
        "created_at": "2017-05-15T22:50:28+00:00",
        "id": 1,
        "name": "exercise",
        "updated_at": "2017-05-15T22:50:28+00:00"
      },
      {
        "board_elements": [
          4, 5 // just indexes of the board elements that have this tag associated with them
        ],
        "created_at": "2017-05-15T22:50:28+00:00",
        "id": 2,
        "name": "exercise",
        "updated_at": "2017-05-15T22:50:28+00:00"
      }
    ]
  }
}
````

#### Add Tag to Board Element
*Request:* `POST /kanban/tags/add?tag_id={tag_id}&board_element_id={board_element_id}`

*Response:*
````javascript
{
  "success": true
}
````

#### Remove Tag from Board Element
*Request:* `DELETE /kanban/tags/add?tag_id={tag_id}&board_element_id={board_element_id}`

*Response:*
````javascript
{
  "success": true
}
````
