# Follows

##Create Follow 

> Create Follow JSON Response (201 - Created):

```json
{
    "message": "Follow created successfuly"
}
```

> Create Follow JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "create-follow-1",
        "message": "Invalid data",
        "description": "Could not create a follow with the provided data"
    }
}
```

This endpoint allows to follow a specific user 

### HTTP Request 

`POST https://endpoint/v1/follows`

### Body parameter 

Parameter | Example | Description
--------- | ------- | -----------
touser (r)| 8 | The identifier of the user to be followed








##Delete Follow 

> Delete Follow JSON Response (200 - Ok):

```json
{
    "message": "Follow deleted successfully"
}
```

> Delete Follow JSON Response (400 - Bad Request): 

```json
{
    "error": {
        "code": "delete-follow-1",
        "message": "Invalid data",
        "description": "The data provided is invalid"
    }
}
```

> Delete Follow JSON Response (404 - Not Found):

```json
{
    "error": {
        "code": "delete-follow-2",
        "message": "Not found",
        "description": "Could not found a follow with the specified data"
    }
}
```

> Delete Follow JSON Response (403 - Forbidden):

```json
{
    "error": {
        "code": "delete-follow-3",
        "message": "Forbidden",
        "description": "You don't ahve the required permissions over this resource"
    }
}
```

This endpoint allows to unfollow a user 

### HTTP Request

`DELETE https://endpoint/v1/follows`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
touser (r)| 8 | The identifier of the user to be unfollowed



