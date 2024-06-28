# Protocol
When a client connects to the server, they are ready to exchange requests

## Integers
Integers are big endian

## Error codes
| Code | Description                                |
| ---- | ------------------------------------------ |
| 0    | Success                                    |
| 1    | Page not found                             |
| 2    | Bad path                                   |
| 3    | Unknown domain                             |

## Client -> Server packets
Fields are in order of how they are received

### Get packet

| Field       | Type                 | Description                                      |
| ----------- | -------------------- | ------------------------------------------------ |
| Packet ID   | Byte                 | Equal to 'G' in 8-bit ASCII                      |
| Domain      | LF-terminated string | String containing the domain of the site         |
| Path        | LF-terminated string | String containing the path of the URL            |

Response:

| Field       | Type                    | Description                                       |
| ----------- | ----------------------- | ------------------------------------------------- |
| Error code  | Byte                    | Rest of the packet is not present if this isn't 0 |
| Length      | 64-bit unsigned integer | Length of the page contents in bytes              |
| Contents    | Bytes                   | Is `Length` bytes long and is the page contents   |


## Bidirectional packets
### Ping packet
| Field       | Type                 | Description                                      |
| ----------- | -------------------- | ------------------------------------------------ |
| Packet ID   | Byte                 | Equal to 'P' in 8-bit ASCII                      |


Response: none
