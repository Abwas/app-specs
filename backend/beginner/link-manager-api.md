# Link Manager API

Build a RESTful API Web Service to manage articles (or links in general) that already have been consumed.

## Table of Contents

- [API Endpoint Reference](#api-endpoint-reference)
- [Functionalities](#functionalities)
- [Credit](#credit)
- [Implementations](#implementations)
- [References](#references)

## API Endpoint Reference

- **Web API Base URL:** `http://localhost:3000/api`

Method | Endpoint | Usage | Returns
:-- | :-- | :-- | :--
`POST` | `/v1/links` | Save a link | Link JSON object
`GET` | `/v1/links` | Get all links | Array with links
`GET` | `/v1/links/:linkId` | Get a link | Link JSON object
`GET` | `/v1/links?category=name` | Get all links of a given category | Array with links
`PATCH` | `/v1/links/:linkId` | Update part of a link | -
`DELETE` | `/v1/links/:linkId` | Delete a link | -

> Use the table above as a quick reference.

## Functionalities

### 1. Save a link

Save a link in your database.

- **URL**:
  - `/v1/links`
- **Method**:
  - `POST`
- **URL Params**:
  - None
- **Data params**:

   ```js
   {
     title: string,     // required
     url: string,       // required
     category: string,  // optional - store the value in lowercase
     rate: number       // required
   }
   ```

- **Success Response**:
  - **Status Code**: `201 Created`
  - **Content**:

  ```js
  {
    "id": "507f1f77bcf86cd799439011",
    "title": "Getting started with ECMAScript 6",
    "url": "http://www.2ality.com/2015/08/getting-started-es6.html",
    "category": "javascript",
    "rate": 5,
    "createdAt": "2015-09-17T12:51:11.159Z", // ISODate format
    "updatedAt": null,
  }
  ```

- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links \
  -X POST \
  -d 'title=Getting started with ECMAScript 6' \
  -d 'url=http://www.2ality.com/2015/08/getting-started-es6.html' \
  -d 'category=javascript' \
  -d 'rate=5'
  ```

### 2. Get all links

Retrieve all links from your database.

- **URL**:
  - `/v1/links`
- **Method**:
  - `GET`
- **URL Params**:
  - None
- **Data params**:
  - None
- **Success Response**:
  - **Status Code**: `200 OK`
  - **Content**:

  ```js
  [
    {
      "id": "507f1f77bcf86cd799439011",
      "title": "Getting started with ECMAScript 6",
      "url": "http://www.2ality.com/2015/08/getting-started-es6.html",
      "category": "javascript",
      "rate": 5,
      "createdAt": "2015-09-17T12:51:11.159Z", // ISODate format
      "updatedAt": null,
    },
    ...
  ]
  ```

- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links
  ```

### 3. Get a link

Retrieve one specific link from your database.

- **URL**:
  - `/v1/links/:linkId`
- **Method**:
  - `GET`
- **URL Params**:
  - **Required**:
    - `linkId=[alphanumeric]`
- **Data params**:
  - None
- **Success Response**:
  - **Status Code**: `200 OK`
  - **Content**:

  ```js
  {
    "id": "507f1f77bcf86cd799439011",
    "title": "Getting started with ECMAScript 6",
    "url": "http://www.2ality.com/2015/08/getting-started-es6.html",
    "category": "javascript",
    "rate": 5,
    "createdAt": "2015-09-17T12:51:11.159Z", // ISODate format
    "updatedAt": null,
  }
  ```

- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links/507f1f77bcf86cd799439011
  ```

### 4. Get all links of a given category

Retrieve all links of a specific category from your database.

- **URL**:
  - `/v1/links?category=name`
- **Method**:
  - `GET`
- **URL Params**:
  - **Required**:
    - `category=[alphanumeric]`
- **Data params**:
  - None
- **Success Response**:
  - **Status Code**: `200 OK`
  - **Content**:

  ```js
  [
    {
      "id": "507f1f77bcf86cd799439011",
      "title": "Getting started with ECMAScript 6",
      "url": "http://www.2ality.com/2015/08/getting-started-es6.html",
      "category": "javascript",
      "rate": 5,
      "createdAt": "2015-09-17T12:51:11.159Z", // ISODate format
      "updatedAt": null,
    },
    ...
  ]
  ```

- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links?category=javascript`
  ```

### 5. Update part of a link

Because we'll need to just update a **part** of our resource, we should use the `PATCH` HTTP method, instead of the most frequently used `PUT` method.

- **OBS**: The `PUT` method should be used when you will update **all** fields of your resource.

- **URL**:
  - `/v1/links/:linkId`
- **Method**:
  - `PATCH`
- **URL Params**:
  - **Required**:
    - `linkId=[alphanumeric]`
- **Data params**:

  ```js
  {
   title: string,     // optional
   url: string,       // optional
   category: string,  // optional - store the value in lowercase
   rate: number       // optional
  }
  ```
- **Success Response**:
  - **Status Code**: `200 OK`
  - **Content**:
    None
- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links/507f1f77bcf86cd799439011 \
  -X PATCH \
  -d 'category=es2015'
  ```

### 6. Delete a link

Delete a specific link in your database.

- **URL**:
  - `/v1/links/:linkId`
- **Method**:
  - `DELETE`
- **URL Params**:
  - **Required**:
    - `linkId=[alphanumeric]`
- **Data params**:
  - None
- **Success Response**:
  - **Status Code**: `200 OK`
  - **Content**:
    None
- **Error Response**:
  - **Status Code**: `500 Internal Server Error`
  - **Content**: 

  ```js
  {
    "error": "Sorry, a problem occurred in our servers."
  }
  ```

- **Sample Call**:

  `cURL`
  
  ```shell
  curl http://localhost:3000/api/v1/links/507f1f77bcf86cd799439011 \
  -X DELETE
  ```

## Credit

- Author: Eric Douglas
- GitHub: [@ericdouglas](https://github.com/ericdouglas)
- Twitter: [@ericdouglas_](https://twitter.com/ericdouglas_)
- Blog: [ericdouglas.github.io](http://ericdouglas.github.io/)

## Implementations

- Author: 
- GitHub:
- Source Code: [link]()
- Live demo: [link]()
- Stack: 

## References

1. [REST API Documentation Best Practices](https://bocoup.com/weblog/documenting-your-api/)
1. [Spotify's Web API Endpoint Reference](https://developer.spotify.com/web-api/endpoint-reference/)
1. [Status Code Definitions](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)
1. [List of HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
1. [HTTP Common Status Code](https://gist.github.com/ericdouglas/b099aa9f07d715aaf3fd)
1. [curl usage explained](http://curl.haxx.se/docs/manual.html)
1. [What's the difference between REST & RESTful](http://stackoverflow.com/a/1568858/2849745)
1. [How cURL commands work](http://docs.rackspace.com/images/api/v2/ci-devguide/content/curl_stuff.html)
