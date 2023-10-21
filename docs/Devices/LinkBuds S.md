# Sony LinkBuds S

## Protocol

**Ambient Sound Control**

!!! info
The words marked as `---- ---- ----` change on every request. Perhaps they are a counter or a nonce.
`000000X0` is the payload number in case of split packets. Packets over 16 bytes are split into
multiple packets.


| Action                  | Type          | Handle | Length | Payload                                               |
| ----------------------- | ------------- | ------ | ------ | ----------------------------------------------------- |
| Enable Noise Cancelling | L2CAP Send    | 0x000B | 32     | 00000000: **09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C** |
|                         |               |        |        | 00000010: **0100 0000 0768 1701 0100 0014 A93C 2540** |
|                         | L2CAP Receive |        | 14     | 00000000: 0BEF 1200 FF5A 0009 40DF DA00 A59A          |
| ASC Off                 | L2CAP Send    | 0x000B | 32     | 00000000: **09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C** |
|                         |               |        |        | 00000010: **0000 0000 0768 1701 0000 0014 A73C 2740** |