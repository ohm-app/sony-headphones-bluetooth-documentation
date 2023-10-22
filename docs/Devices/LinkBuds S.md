# Sony LinkBuds S

## Protocol

!!! info
    The words marked as `---- ---- ----` change on every request. Perhaps they are a counter or a nonce.

!!! info
    Packets over 16 bytes are split into multiple packets within the same message.
    If none of the table columns change except for the payload, then the packets are part of the same message.

The tables below show the packets sent and received for performing a given action.
The tables are ordered by the time the Bluetooth messages were sent or received, with the first message at the top.

### Ambient Sound Control (AmSC)

| Action                  | Type          | Handle | Length | Payload (Hex Decimals)                  |
| ----------------------- | ------------- | ------ | ------ | --------------------------------------- |
| Enable Noise Cancelling | L2CAP Send    | 0x000B | 32     | 09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C |
|                         |               |        |        | 0100 0000 0768 1701 0100 0014 A93C 2540 |
|                         | L2CAP Receive |        | 14     | 0BEF 1200 FF5A 0009 40DF DA00 A59A      |
| AmSC Off                | L2CAP Send    | 0x000B | 32     | 09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C |
|                         |               |        |        | 0000 0000 0768 1701 0000 0014 A73C 2740 |