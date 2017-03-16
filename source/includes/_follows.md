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








##Get Follow Feed

> Get Follow Feed JSON Response (200 - Ok):

```json
{
    "followers": [
    {
        "id": 2,
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "username": "diefer2"
    },
    {
        ...
    }
    ]
}
```

This endpoint allows to get the follow feed of the logged in user 

### HTTP Request 

`GET https://endpoint/v1/follows/feed`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of follows to be retrieved
offset | 20 | the item position from where the new follows are going to be retrieved 









##Get Followers 

> Get Followers JSON Response (200 - Ok):

```json
{
    "followers": [
    {
        "id": 2,
        "name": "Ferch Illera",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "username": "diefer2"
    }
    ],
    {
        ...
    }
}
```

This endpoints allows to get the followers of a specific user 

### HTTP Request 

`GET https://endpoint/v1/follows/followers/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 3 | The id of the user you want to get the followers 

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of follows to be retrieved
offset | 20 | the item position from where the new follows are going to be retrieved 











## Get Followings

> Get Followings JSON Response (200 - Ok):

```json
{
    "followings": [
    {
        "id": 2,
        "name": "Ferch Illera",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "username": "diefer2"
    }
    ],
    {
        ...
    }
}
```

This endpoint allows to get the users that a specific user is following 

### HTTP Request 

`GET https://endpoint/v1/follows/following/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 3 | The id of the user you want to get the following users

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of follows to be retrieved
offset | 20 | the item position from where the new follows are going to be retrieved 




