# Comments

##Create Comment

> Create Comment JSON Response (201 - Created): 

```json
{
    "message": "Comment created successfully"
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






