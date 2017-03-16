# Likes 

##Create Like

> Create Like JSON Response (201 - Created): 

```json
{
    "message": "Like created successfully"
}
```

> Create Like JSON Response (400 - Bad Request): 

```json
{
    "error": {
        "code": "create-like-1",
        "message": "Invalid data",
        "description": "Invalid data provided"
    }
}
```

This endpoint allows to like a specific post

### HTTP Request 

`POST https://endpoint/v1/likes`

### Body parameter 

Parameter | Example | Description
--------- | ------- | -----------
touser (r)| 8 | The identifier of the user that made the post
post (r) | 3 | The identifier of the post 











##Delete Like

> Delete Like JSON Response (200 - Ok):

```json
{
    "message": "Like deleted successfully"
}
```

> Delete Like JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "delete-like-1",
        "message": "Invalid data",
        "description": "Invalid data provided"
    }
}
```

> Delete Like JSON Response (404 - Not found):

```json
{
    "error": {
        "code": "delete-like-2",
        "message": "Not found",
        "description": "Like not found with the specified id"
    }
}
```

> Delete Like JSON Response (403 - Forbidden): 

```json
{
    "error": {
        "code": "delete-like-3",
        "message": "Forbidden",
        "description": "You don't have write permissions on this resource"
    }
}
```

this endpoint allows to delete a like from a post 

### HTTP Request 

`DELETE https://endpoint/v1/likes/`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
postid (r) | 8 | The id of the post you want to remove the like 











##Get Likes Feed 

> Get Likes Feed JSON Resposne (200 - Ok):

```json
{
    "likes": [
    {
        "compositeid": 21,
        "createdat": "2017-01-28 14:04:36",
        "fromuser": {
            "id": 2,
            "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
            "username": "diefer2"
        },
        "id": 1,
        "post": {
            "id": 1,
            "thumbnailimageurl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg"
        },
        "touser": 1
    },
    {
        ...
    }
    ]
}
```

This endpoint allowes to get the likes feed of the logged in user 

### HTTP Request 

`GET https://endpoint/v1/likes/feed`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of likes to be retrieved
offset | 20 | the item position from where the new likes are going to be retrieved 











##Get Likes of Post 

> Get Likes of Post JSON Response (200 - Ok):

```json
{
    "users": [
    {
        "id": 2,
        "name": "Ferch Illera",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "username": "diefer2"
    },
    {
        ...
    }
    ]
}
```

This endpoint allowes to get the likes of a specific post 

### HTTP Request 

`GET https://endpoint/v1/likes/forpost/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 2 | The id of the post 

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of likes to be retrieved
offset | 20 | the item position from where the new likes are going to be retrieved 





















