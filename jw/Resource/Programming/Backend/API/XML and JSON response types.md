## Introduction
When it comes to displaying output, an [[API]] developer should always allow the client to request the preferred content type, such as [[JSON]] or [[XML]]. Clients can do this by supplying an additional header called `Accept` in the request header. There is information here [[HTTP response types]]. In this way, the client has full flexibility to use the content in the way they want to.
## Request headers
Client applications need to send `Accept` request headers with every [[HTTP]] request to receive the output in [[JSON]] or [[XML]]. For example:

| Response type | Request header |
| :-------------- | :----------- |
| JSON | `Accept: application/json`|
| XML | `Accept: application/xml`<br>`Accept: text/xml`|

## JSON vs. XML
JSON gained popularity because it's very simple and lightweight. And creating JSON data or parsing it is easier than XML. However, XML has its own advantages too. XML is more readable and supports data attributes that are not possible in JSON. 

| [[JSON]]                                                                                                                     | [[XML]]                                                                                                                                                                                                                                                                               |
|:------------------------------------------------------------------------------------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
| JSON or __Javascript Object Notation__ is a lightweight and dependency-free data format.                                 | XML or __Extensible Markup Language__ is a powerful, tag-based data format. It is similar to HTML. XML data can be fairly complex.                                                                                                                                            |    
| The size of JSON data is smaller than XML. So, it takes less bandwidth.                                                  | XML data is lengthier than JSON and takes up more bandwidth.                                                                                                                                                                                                                  | 
| JSON data is like keys and values.<br>{<br>"author": "Jack London"<br>"title": "Seawolf"<br>}                            | XML is completely-tag based, it does not have key-value pairs like JSON.<br>`<?xml version="1.0" encoding="UTF-8"?>`<br>`<root>`<br>`    <author>Jack London</author>`<br>`    <title>Seawolf</title>`<br>`</root>`                                                           |     |
| Representing array elements is simpler in JSON. Here’s an example:<br>{<br>"items": [1,2,3,4,5]<br>}                     | `<?xml version="1.0" encoding="UTF-8">`<br>`<root>`<br>    `<items>`<br>        `<element>1</element>`<br>        `<element>2</element>`<br>        `<element>3</element>`<br>        `<element>4</element>`<br>        `<element>5</element>`<br>    `</items>`<br>`</root>` |     |
| Generating and parsing JSON data is faster than XML and this conversion process requires less memory and computer power. | Generating and parsing XML is a complex process, it usually takes more processing power and memory.                                                                                                                                                                           |     |
| There is no way to include comments in JSON data.                                                                                                                                                                                                                             | XML data can include comments.    |
