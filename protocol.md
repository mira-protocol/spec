# Protocol
When a client connects to the server, they are ready to exchange requests

## Notes
Integers are big endian

## Client -> Server packets
### GET packet

| Field       | Type                 | Description                                      |
| ----------- | -------------------- | ------------------------------------------------ |
| Packet ID   | Byte                 | Equal to 'G' in ASCII                            |
| Domain      | LF-terminated string | String containing the domain of the site         |
| Path        | LF-terminated string | String containing the path of the URL            |

Response:

| Field       | Type                    | Description                                       |
| ----------- | ----------------------- | ------------------------------------------------- |
| Error code  | Byte                    | Rest of the packet is not present if this isn't 0 |
| Length      | 64-bit unsigned integer | Length of the page contents                       |
| Contents    | Bytes                   | Is `Length` bytes long and is the page contents   |


