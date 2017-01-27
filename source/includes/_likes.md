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








