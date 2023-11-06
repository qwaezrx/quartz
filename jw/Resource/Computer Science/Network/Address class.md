
## Address class system

>A way of defining how the global IP address space is split up

### Class A
First octet is used for the [[Network ID]] and the rest for [[Host ID]]
### Class B
First 2 octet is used for the [[Network ID]] and the rest for the [[Host ID]]
### Class C
First 3 octet is used for the [[Network ID]] and the rest for the [[Host ID]]

| Class | Left-most bit | Starting IP address | Last IP address |
| ----- | ------------- | ------------------- | --------------- |
| A     | 0xxx          | 0.0.0.0             | 127.255.255.255 |
| B     | 10xx          | 128.0.0.0           | 191.255.255.255 |
| C     | 110x          | 192.0.0.0           | 223.255.255.255 |
| D     | 1110          | 224.0.0.0           | 239.255.255.255 |
| E     | 1111          | 240.0.0.0           | 255.255.255.255                |

