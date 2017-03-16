# Posts 

##Create Post 

> Create Post JSON Response (201 - Created):

```json
{
    "post": {
        "averageimagecolor": [
            0,
            0,
            255
        ],
        "commenterscount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "user_id": 1,
        "userinfo": {
            "id": 1 
            "name": "Diego",
            "username": "diefer91", 
            "photourl": null 
        }
    }
}
```

> Create Post JSON Response (400 - Bad Request):

```json
{
    "error": {
        "code": "create-posts-1",
        "description": "The image url is required",
        "message": "No image url"
    }
}
```

This endpoint allows to create a post 

### HTTP Request 

`POST http://endpoint/v1/posts`

### Body parameter 

Parameter | Example | Description
--------- | ------- | -----------
imageurl (r)| http://www.google.com/image.jpg | The url of the image 
thumbnailimageurl (r) | http://www.google.com/image.jpg | The url of the thumbnail image 
description | This is my dog! | The description of the post 
type (r) | photo | For the initial release only 'photo' is supported
averagecolorarray | [100,200,300] | The average color of the image
hashtags | [labrador, bogota] | The post hashtags







##Get Post 

> Get Post JSON Response (200 - Ok):

```json
{
    "post": {
        "averageImageColor": [
            0,
            0,
            255
        ],
        "commentersCount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "enabled": true,
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "user_id": 1,
        "userinfo": {
            "id": 1 
            "name": "Diego",
            "username": "diefer91", 
            "photourl": null 
        }

    }
}
```

> Get Post JSON Response (404 - Not Found)

```json
{
    "error": {
        "code": "get-posts-1",
        "description": "Could not find a post with the specified id",
        "message": "No post found"
    }
}
```

This endpoint allows to get a post by its id 

### HTTP Request

`GET http://endpoint/v1/posts/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 12 | The id of the post








##Update Post 

> Update Post JSON Response (200 - Ok):

```json
{
    "post": {
        "averageImageColor": [
            0,
            0,
            255
        ],
        "commentersCount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "enabled": true,
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "updatedat": "2017-01-18 01:24:40",
        "user_id": 1
    }
}
```

> Update Post JSON (403 - Forbidden):

```json
{
    "error": {
        "code": "update-post-4",
        "description": "The resource could not be modified because you don't have the neccesary permissions",
        "message": "Forbidden"
    }
}
```

> Update Post JSON (404 - Not Found):

```json
{
    "error": {
        "code": "update-post-1",
        "description": "Could not found the post with the specified id",
        "message": "Not Found"
    }
}
```

This endpoint allows to update the post (Only the description and hashtags fields)

### HTTP Request

`PUT http://endpoint/v1/posts/:id`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 12 | The id of the post

### Body Parameters 

Parameter | Example | Description
--------- | ------- | -----------
description | Wonderful dog! | The new description of the post 
hashtags | [labrador, beautiful] | The new hashtags 











##Disable Post 

> Disable Post JSON Response (200 - Ok):

```json
{
    "message": "Post disabled successfully"
}
```

> Disable Post JSON Response (404 - Not Found):

```json
{
    "error": {
        "code": "disable-post-1",
        "description": "Could not found the post with the specified id",
        "message": "Not Found"
    }
}
```

> Disable Post JSON Response (403 - Forbidden):

```json
{
    "error": {
        "code": "disable-post-4",
        "description": "The resource could not be modified because you don't have the neccesary permissions",
        "message": "Forbidden"
    }
}
```

This endpoint allows to disable a post by its id. We will never delete data from the database, 
so this endpoint sets the `enable` flag of the post to `false`

### HTTP Request 

`PUT http://endpoint/v1/posts/:id/disable`

### URL Parameters 

Parameter | Example | Description
--------- | ------- | -----------
id | 12 | The id of the post








##Get Main Feed 

> Get Main Feed JSON Response (200 - Success):

```json
{
    "posts": [{
        "averageImageColor": [
            0,
            0,
            255
        ],
        "commentersCount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "enabled": true,
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "updatedat": "2017-01-18 01:24:40",
        "user_id": 1,
        "userinfo": {
            "username": diefer91,
            "name": "Diego Vidal",
            "thumbnailphotourl": "http://www.google.com/image1.jpg"
        }
    }, 
    { 
        ...
    }
    ]
}
```

This endpoint retrieves the main feed for the user (Posts from people he is following and his own posts)

### HTTP Request 

`GET http://endpoint/v1/posts/mainfeed`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of posts to be retrieved
offset | 100 | The post position from where the query will return posts 







##Search Posts 

> Search Post JSON Response (200 - Ok): 

```json
{
    "posts": [{
        "averageImageColor": [
            0,
            0,
            255
        ],
        "commentersCount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "enabled": true,
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "updatedat": "2017-01-18 01:24:40",
        "user_id": {
            "id": 10,
            "name": "Diego Vidal",
            "username": "diefer91",
            "thumgnailphotourl": "http://www.google.com/image1.jpg"
        }
    }, 
    { 
        ...
    }
    ]
}
```

This endpoints allows to search for posts, can be filtered by hashtag. 

### HTTP Request 

`GET https://endpoint/v1/posts/search`

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of posts to be retrieved
offset | 100 | The post position from where the query will return posts 
hashtag | labrador | The hashtag to be used as a filter - you can also send a username in this field (ej: @diefer91)










##Get Presigned S3 Url 

> Get PresigneUrl JSON Response (200 - Ok):

```json
{ 
    "presignedurllarge": "https://sdfsdfsdfdf........",
    "presignedurlthumbnail": "https://sdsdfsdfsdfsdf......"
}
```

This endpoint allows to get the presigned urls to use to upload the large and thumbnail post images. 

### HTTP Request 

`GET https://endpoint/v1/posts/presignedurl`










##Get Posts of User 

> Get Posts of User JSON Response When fulldetails = true (200 - Ok):

```json
{
    "posts": [{
        "averageImageColor": [
            0,
            0,
            255
        ],
        "commentersCount": 0,
        "createdat": "2017-01-18 01:24:40",
        "description": "desss",
        "hashtags": [
            "#pomerania",
            "#labrador"
        ],
        "id": 3,
        "imageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "likersCount": 0,
        "thumbnailImageUrl": "http:\/\/www.car-brand-names.com\/wp-content\/uploads\/2015\/04\/BMW-logo-2.jpg",
        "type": "photo",
        "user_id": {
            "id": 10,
            "name": "Diego Vidal",
            "username": "diefer91",
            "photourl": "http://www.google.com/image1.jpg"
        }  
    }, 
    { 
        ...
    }
    ]
}
```

> Get Posts of User JSON Response When fulldetails = false (200 - Ok):

```json
{
    "posts": [{
        "id": 10,
        "thumbnailimageurl": "http://asdasdasd...",
        "averageImageColor": [
            0,
            0,
            255
        ]
    },
    {
        "id": 10,
        "thumbnailimageurl": "http://asdasdasd...",
        "averageImageColor": [
            0,
            0,
            255
        ]
    }
    ]
}
```


This endpoint allows to get the posts of a specific user. The posts can be retrieved as the thumbnail representation (used for cases where you only want to display the thumbnails), or as the full-details post. 

### HTTP Requesrt 

`GET https://endpoint/v1/posts/thumbnails` 

### Query Parameters 

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of posts to be retrieved
offset | 100 | The post position from where the query will return posts 
userid | 20 | the id of the user you want to get the posts 
fulldetails | true/false | if true, all the details of the post will be retrieved. If false, or not provided, just the thumbnail representation of the post will be retrieved 









##Get Posts Tagged With User 

```json
{
    "posts": [{
        "id": 10,
        "thumbnailimageurl": "http://asdasdasd...",
        "averageImageColor": [
            0,
            0,
            255
        ]
    },
    {
        "id": 10,
        "thumbnailimageurl": "http://asdasdasd...",
        "averageImageColor": [
            0,
            0,
            255
        ]
    }
    ]
}
```

This endpoint allows to get the posts where a specific user has been tagged 

### HTTP Request 

`GET https://endpoint/v1/posts/tagged/:username`

Parameter | Example | Description
--------- | ------- | -----------
count | 30 | The number of posts to be retrieved
offset | 100 | The post position from where the query will return posts 
username | diefer91 | the username of the user








