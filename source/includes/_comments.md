# Comments

##Create Comment

> Create Comment JSON Response (201 - Created): 

```json
{
    "comment": {
        "createdat": "2017-02-24 23:30:42",
        "fromuser": 1,
        "fromuserinfo": {
            "name": "Ferch Illera",
            "thumbnailphotourl": null,
            "username": "diefer_1"
        },
        "id": 12,
        "post": 1,
        "postinfo": null,
        "text": "Sacissss",
        "touser": 1,
        "touserinfo": null
    }
}
```

> Create Like JSON Response (400 - Bad Request): 

```json
{
    "error": {
        "code": "create-comment-1",
        "message": "Invalid data",
        "description": "Invalid data provided"
    }
}
```

This endpoint allows to create a comment in a specific post 

### HTTP Request 

`POST https://endpoint/v1/comments`

### Body parameter 

Parameter | Example | Description
--------- | ------- | -----------
touser (r)| 8 | The identifier of the user that made the post
post (r) | 3 | The identifier of the post 
text (r) | Bonito labrador! | The comment











##Delete Comment

> Delete Comment JSON Response (200 - Ok):

```json
{
    "message": "Comment deleted successfully"
}
```

> Delete Comment JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "delete-comment-1",
        "message": "Invalid data",
        "description": "Invalid data provided"
    }
}
```

> Delete Comment JSON Response (404 - Not found):

```json
{
    "error": {
        "code": "delete-comment-1",
        "message": "Invalid data",
        "description": "Invalid data provided"
    }
}
```

> Delete Comment JSON Response (403 - Forbidden):

```json
{
    "error": {
        "code": "delete-comment-2",
        "message": "Forbidden",
        "description": "You don't have the permissions to access this resource"
    }
}
```

This endpoint allows to delete a comment 

### HTTP Request 

`DELETE https://endpoint/v1/comments/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id (r)| 8 | The identifier of the comment










##Get Comments Feed 

> Get Comments Feed JSON Response (200 - Ok): 

```json
{
    "comments": [
    {
        "createdat": "2017-01-26 22:57:47",
        "fromuser": {
            "id": 1,
            "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
            "username": "diefer1"
        },
        "id": 1,
        "post": {
            "id": 1,
            "thumbnailimageurl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg"
        },
        "text": "Sisaas",
        "touser": 1
    },
    {
        ...
    }
    ]
}
```

This endpoint allows to get the comments feed of the logged in user 

### HTTP Request 

`GET https://endpoint/v1/comments/feed`

### Query Parameters

Parameter | Example | Description
--------- | ------- | -----------
count| 30 | The number of comments to be retrieved 
offset | 60 | The comments position from where the new comments will be retrieved 









##Get Comments of Post 

> Get Comments of Post JSON Response (200 - Ok):

```json
{
    "comments": [{
        "createdat": "2017-02-24 23:30:42",
        "fromuser": 1,
        "fromuserinfo": {
            "name": "Ferch Illera",
            "thumbnailphotourl": null,
            "username": "diefer_1"
        },
        "id": 12,
        "post": 1,
        "postinfo": null,
        "text": "Sacissss",
        "touser": 1,
        "touserinfo": null
    },
    {
        ...
    }
    ]
}
```

This endpoint allows to get the comments of a specific post 

### HTTP Request 

`GET https://endpoint/v1/comments/forpost/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id| 3 | The id of the post you want to get the comments

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count| 30 | The number of comments to be retrieved 
offset | 60 | The comments position from where the new comments will be retrieved 









