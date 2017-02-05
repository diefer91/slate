---
title: Pets Social iOS & Android Clients API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - posts
  - likes
  - follows
  - comments
  - mainadds
  - errors

search: true
---

# Pets Social iOS & Android API Reference

Welcome to the Pets Social API! Use this API to access all the endpoints for the Pets Social iOS and Android App. 

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

Pets Social uses an API Key to allow access to the endpoints. If you don't have an API Key, please contact the administrator to request one.

Pets Social expects for the API key to be included in all API requests to the server in a header that looks like the following:

`apikey: woofwoofwoof`

<aside class="notice">
You must replace <code>woofwoofwoof</code> with the app API Key.
</aside>

Almost all of the Pets Social endpoints require an authenticated user. This information must be provided in a header that looks like the following:

`cookie: vapor-auth=asdjasldjasjdvjdnjg==`

This cookie will be sent to the client in the header `set-cookie` in the response of the `login` endpoint.

# Users 

## Create User

> Create User JSON Response (201 - Created):

```json
{
    "user": {
        "createdat": "2017-01-17 13:51:44",
        "email": "diefer_2@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": null,
        "id": 6,
        "likedpostsids": null,
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 13:51:44",
        "username": "diefer1"
    }
}
```

> Create User JSON Response (400 - Bad Request): 

```json
{
    "error": 
    {
        "code": "user-create-1",
        "message": "Invalid Name",
        "description": "Names must have only alphabetic characters and have between 3 and 64 characters"
    }
}
```

> Create User JSON Response (500 - Internal Server Error):

```json
{
    "error": {
        "code": "user-create-5",
        "description": "A server error ocurred when trying to save the user in the database: The operation could not be completed. (PostgreSQL.DatabaseError error 1.)",
        "message": "Server error"
    }
}
```

This endpoint creates a new user. 

### HTTP Request

`POST https://endpoint/v1/users`

### Body Parameters

Parameter | Example | Description
--------- | ------- | -----------
name (r)| Diego Vidal | Only alphabetic characters. Between 3 - 64 characters long.
email (r)| diego@test.com | Must be a valid email. Between 6 - 64 characters long.
password (r)| Abcd1234 | Require one numeric and one uppercase character. Between 3 - 18 characters long.
username (r)| diego10 | Must contain only letters, numbers, and _-. Between 3 - 18 characters long.
photourl | ....... | the url of the photo 
thumbnailphotourl | ........ | the url of the thumbnail photo

<aside class="success">
If everything is ok, a new user must be created!
</aside>










## Login User

> Login User JSON Response (200 - Ok): 

```json
{
    "user": {
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    }
}
```

> Login User JSON Response (404 - Not Found):

```json
{
    "code": 404,
    "error": true,
    "message": "No user found with those credentials",
    "metadata": null
}
```

> Login User JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "user-login-1",
        "description": "Please provide an email",
        "message": "Invalid login credentials"
    }
}
```

This endpoint logs in the user.

### HTTP Request

`POST https://endpoint/v1/users/login`

### Body Parameters

Parameter | Example | Description
--------- | ------- | -----------
email | diefer10 | Can be the email or the username of the user.
password | Abcd1234 | the password of the user.

### HTTP Response Headers

When the login is successfull, a cookie will be returned to the client in the response headers, it looks like the following: 

`set-cookie: vapor-auth=sdiwjdjndcwwo==`

<aside class="notice">
THE CLIENT MUST SEND THIS COOKIE IN ALL THE NEXT REQUESTS IT MADES, AS DISCUSSED IN THE AUTHENTICATION SECTION OF THE DOCS!
</aside>

##Logout User

> Logout User JSON Response (200 - Ok): 

```json
{
    "message": "Logout Successfull"
}
```

This endpoint logs out the user. 

### HTTP Request

`POST https://endpoint/v1/users/logout`











##Get User 

> Get User JSON Response (200 - OK):

```json
{
    "user": {
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    }
}
```

> Get User JSON Response (404 - Not Found): 

```json
{
    "error": {
        "code": "get-user-1",
        "description": "Could not find a user with the specified id",
        "message": "No user found"
    }
}
```

This endpoint gets a user by its id 

### HTTP Request 

`GET https://endpoint/v1/users/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 12 | The id of the user















##Get User From Cookie 

> Get User from Cookie JSON Response (200 - Ok):

```json
{
    "user": {
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    }
}
```

This endpoint allows to get a user from a cookie

### HTTP Request

`GET https://endpoint/v1/users/cookie`

### Header Parameters 

Parameter | Example | Description
--------- | ------- | -----------
cookie | sdf86sdfdsf86f8 | The cookie of the user to be retrieved










##Update Users 

> Update User JSON Response (200 - Ok): 

```json
{
    "user": {
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    }
}
    
```

This endpoint allows to update the user information. For now, only updating the name is supported.

### HTTP Request

`PUT https://endpoint/v1/users`

### Body Parameters 

Parameter | Example | Description
--------- | ------- | -----------
name | diego vidal | The updated name of the user








##Change Password 

> Change Password JSON Response (200 - Ok): 

```json
{ 
    "message": "password updated successfully"
}
```

> Change Password JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "change-pass-4",
        "message": "Invalid data",
        "description": "The passwords provided are invalid"
    }
}
```

This endpoint allows to change the user's password 

### HTTP Request 

`POST https://endpoint/v1/users/changepassword`

### Body Parameters 

Parameter | Example | Description
--------- | ------- | -----------
oldpassword | Abcd1234 | The actual password of the user 
newpassword | Dfghj5893 | The new password of the user 






##Search Users 

> Search Users JSON Response (200 - Ok):

```json
{
    "users": [{
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    },
    {
        "createdat": "2017-01-17 11:58:06",
        "email": "diefer_1@hotmail.com",
        "enabled": true,
        "followerscount": 0,
        "followingids": [

        ],
        "id": 1,
        "likedpostsids": [

        ],
        "name": "Ferch Illera",
        "photourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "thumbnailphotourl": "https:\/\/upload.wikimedia.org\/wikipedia\/en\/thumb\/a\/a3\/Audi_Logo.svg\/220px-Audi_Logo.svg.png",
        "updatedat": "2017-01-17 11:58:06",
        "username": "diefer3"
    }]
}
```

This endpoint allows to search and filter users. 

### HTTP Request 

`GET https://endpoint/v1/users/search`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 20 | The numbers of items to be retrieved 
offset | 10 | The item from which the results are going to be sent
username | diefer1 | the username to use as a filter

