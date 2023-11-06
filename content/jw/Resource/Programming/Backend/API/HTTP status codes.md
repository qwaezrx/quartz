Sending appropriate [[HTTP]] status codes  with every [[API]] response is essential. Every status code has meaning, so you should choose the most appropriate one based on the situation.

| Status code range | Meaning | Examples |
| :------------------ | :-------- | :---------|
|`100-199`| Mainly used to pass on some information. | `102` - Processing |
	| `200-299` | Success codes. | `200` - Successful(`GET, PUT, PATCH, DELETE`)<br> `201` - Created(`POST`) |
| `300-399` | Redirection codes. | `301` - Permanently moved
| `400-499` | Client error codes. | `404` - Not Found<br>`400` - Bad Request<br>`401` - Unauthorized<br>`403` - Forbidden
| `500-599` | Server side error codes. | |

## Additional Resources

- [List of HTTP status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
