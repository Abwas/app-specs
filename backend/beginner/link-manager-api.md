# Link Manager API

System to manage articles (or links in general) that already have been consumed.

## Functionalities

### API Endpoint Reference

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
