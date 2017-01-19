# Activities

##Create Activity 

> Create Activity JSON Response (201 - Created): 

```json
{
    "message": "Activity created successfully"
}
```

This endpoint allows to create an activity (like, follow or comment)

### HTTP Request 

`POST http://petssocialdev.herokuapp.com/v1/activities`

### Body Parameters 

Parameter | Example | Description
--------- | ------- | -----------
touser | 4 | The id of user you are interacting with. 
type | like | the type of interaction (can be like, follow or comment)
post | 3 | the id of the post you are interacting with (NOT APPLICABLE TO 'FOLLOW' ACTIVITIES)
content | Your dog is so pretty! | The comment made on the post (ONLY APPLICABLE TO 'COMMENT' ACTIVITIES)










##Unfollow User 

> Unfollow User JSON Response (200 - Ok): 

```json
{ 
    "message": "User unfollowed successsfully"
}
```

> Unfollow User JSON Response (404 - Not Found): 

```json
{ 
    "error": {
        "code": "unfollow-user-1",
        "message": "Not found",
        "description": "A user with the specified id could not be found"
    }
}
```

This endpoint allows to unfollow a specific user 

### HTTP Request 

`DELETE http://petssocialdev.herokuapp.com/v1/activities/unfollow/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 4 | The id of user you want to unfollow









##Unlike Post 

> Unlike Post JSON Response (200 - Ok):

```json
{
    "message": "Post unliked successfully"
}
```

> Unlike Post JSON Response (404 - Not Found): 

```json
{ 
    "error": {
        "code": "unlike-post-1",
        "message": "Not found",
        "description": "A post with the specified id could not be found"
    }
}
```

This endpoint allows to unlike a specific post 

### HTTP Request 

`DELETE http://petssocialdev.herokuapp.com/v1/activities/unlike/:id`

### URL Paramaters 

Parameter | Example | Description
--------- | ------- | -----------
id | 3 | the id of the post you want to unlike








##Delete Comment 

> Delete Comment JSON Response (200 - Ok): 

```json
{
    "message": "Comment deleted successfully"
}
```

> Delete Comment JSON Response (404 - Not Found):

```json
{ 
    "error": {
        "code": "delete-comment-1",
        "message": "Not found",
        "description": "A comment with the specified id could not be found"
    }
}
```

this endpoint allows to delete a comment 

### HTTP Request 

`DELETE http://petssocialdev.herokuapp.com/v1/activities/uncomment/:id`

### URL Paramaters 

Parameter | Example | Description
--------- | ------- | -----------
id | 3 | the id of the comment you want to delete








##Get Activities for Post 

> Get Activities for Post JSON Response (200 - Ok):

```json
{
    "activities": [{
        "content": null,
        "createdat": "2017-01-19 13:24:33",
        "enabled": true,
        "fromuser": {
            "id": 10,
            "thumbnailphotourl": "http://www.google.com/image1.jpg",
            "name": "Diego Vidal"
        },
        "id": 1,
        "post": null,
        "touser": 2,
        "type": "follow",
        "updatedat": "2017-01-19 13:24:33"
    },
    {
        ...
    }
    ]
}
```

> Get Activities for Post JSON Response (400 - Bad Request):

```json
{
    "error": {
        "status": "get-activities-1",
        "message": "Wrong activity type", 
        "description": "The supported activity types are like, follow and comment"
    }
}
```

This endpoint allows to get the activities related to a specific post (For example, if you want to get the likers or comments for a post)

### HTTP Request 

`GET http://petssocialdev.herokuapp.com/v1/activities/forpost/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 3 | the id of the post 

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 20 | The number of activities to be retrieved 
offset | 30 | The activity position from where the new activities will be retrieved 
type | like | The type of activities to be retrieved (like, comment, follow)








##Get Activity Feed 

> Get Activity Feed JSON Response (200 - Ok):

```json
{
    "activities": [{
        "content": null,
        "createdat": "2017-01-19 13:24:33",
        "enabled": true,
        "fromuser": {
            "id": 10,
            "thumbnailphotourl": "http://www.google.com/image1.jpg",
            "name": "Diego Vidal"
        },
        "id": 1,
        "post": {
            "id": 10,
            "thumbnailimageurl": "http://www.google.com/image1.jpg"
        },
        "touser": 2,
        "type": "follow",
        "updatedat": "2017-01-19 13:24:33"
    },
    {
        ...
    }
    ]
}
```

This endpoints retrieves the activity feed for the user 

### HTTP Request 

`GET http://petssocialdev.herokuapp.com/v1/activities/feed`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 20 | The number of activities to be retrieved 
offset | 30 | The activity position from where the new activities will be retrieved 







