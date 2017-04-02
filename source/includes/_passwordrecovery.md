# Password Recovery Request 

##Create Password Recovery Request 

> Create Recovery Request JSON Response (200 - Ok):

```json
{
    "message": "Password recovery created successfully! An email has been sent to your account with the instructions to recover your password"
}
```

This endpoint allows to create a password recovery request 

### HTTP Request 

`POST https://endpoint/v1/passwordrecoveryrequests`

### Body parameter 

Parameter | Example | Description
--------- | ------- | -----------
email (r)| diefer_91@hotmail.com | The email of the user that wants to recover the password





