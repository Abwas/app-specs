# Link Manager API

System to manage articles (or links in general) that already have been consumed.

## API Endpoint Reference

- **Web API Base URL:** `http://localhost:3000/api`

Method | Endpoint | Usage | Returns
:-- | :-- | :-- | :--
`POST` | `/v1/links` | Save a link | Link JSON object
`GET` | `/v1/links` | Get all links | Array with links
`GET` | `/v1/links/:linkID` | Get a link | Link JSON object
`GET` | `/v1/links?category=name` | Get all links of a given category | Array with links
`PATCH` | `/v1/links/:linkID` | Update part of a link | Link JSON object
`DELETE` | `/v1/links/:linkID` | Delete a link | -
`DELETE` | `/v1/links/:categoryName` | Delete links of a given category | -

Use the table above as a quick reference.

## Functionalities

### 1. Save a link

Save a link in your database.

- **URL**:
  - `/v1/links`
- **Method**:
  - `POST`
- **Data params**:

   ```js
   {
     title: string,     // required
     url: string,       // required
     category: string,  // optional
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
    "category": "JavaScript",
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
curl http://localhost:3000/api/books \
-d 'title=cURL Book' \
-d 'genre=Technical' \
-d 'author=Eric Douglas'
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
