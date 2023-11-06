---
aliases:
  - JavaScript Object Notation
extended from: "[[JavaScript]]"
tags:
  - CS/Data-Format
---

_JSON_ is an open standard file format and data interchange format that uses human-readable text to store and transmit data objects consisting of _attribute-value pairs_ and _arrays_ (or other serializable values). It is common data format with diverse uses in electronic data interchange, including that of web applications with servers.

- _language-independent_ data format
- derived from [[JavaScript]]
- filename extension = `.json`
- internet media type = `application/json`


## Syntax
---

JSON representation describing a person:
```json
{
  "first_name": "John",
  "last_name": "Smith",
  "is_alive": true,
  "age": 27,
  "address": {
    "street_address": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postal_code": "10021-3100"
  },
  "phone_numbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [
    "Catherine",
    "Thomas",
    "Trevor"
  ],
  "spouse": null
}
```

## See More
---
- https://ko.wikipedia.org/wiki/JSON
- [json.org](https://www.json.org/json-en.html)