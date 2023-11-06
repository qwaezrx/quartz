One endpoint can perform multiple tasks. [[HTTP]] methods or request types tell the [[API]] endpoint what it should do with the resources.

| HTTP method | Action |
| :--------------|:------|
| `GET` | Returns the requested resource. If not found, returns a `404 Not Found` status code. |
| `POST` | Creates a [[Record]]. The `POST` request always comes with HTTP request body(aka. payload), which contains JSON or Form URL encoded data. Although you can create multiple resources with a single `POST` call, it is not considered a best practice to do so. |
| `PUT` | Instructs API to replace the resource. A `PUT` request usually supplies all data for a particular resource so that the API developer can fully replace that resource with the provided data. A `PUT` request deals with a single resource.|
| `PATCH` | Tells API to update a part of the resource. A `PATCH` request also deals with a single [[Record]].|
| `DELETE` | Instructs API to delete a resource. |
