---
aliases:
  - JSON-RPC 2.0
---

_JSON-RPC_ is a stateless, light-weight remote procedure call ([[RPC]]) protocol. Primarily this specification defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over http, or in many various message passing environments. It uses [[JSON]] as data format.

## Request Object
---
`jsonrpc` = "2.0"
`method`
`params`
`id`

## Response Object
---
`jsonrpc` = "2.0"
`result`
`error`
`id`
### Error Object
`code`
`message`
`data`

## Resources
---
- https://www.jsonrpc.org
- https://www.jsonrpc.org/specification

## See More
---
- https://en.wikipedia.org/wiki/Remote_procedure_call
