# Sony LinkBuds S

## Protocol

**Ambient Sound Control**

!!! info
    The words marked as `---- ---- ----` change on every request. Perhaps they are a counter or a nonce.

!!! info
    Packets over 16 bytes are split into multiple packets within the same message.
    If none of the table columns change except for the payload, then the packets are part of the same message.

The below table shows the packets sent and received when enabling noise cancelling and disabling ambient sound control.
The table is ordered by the time the Bluetooth messages were sent or received, with the first message at the top.

| Action                  | Type          | Handle | Length | Payload                                 |
| ----------------------- | ------------- | ------ | ------ | --------------------------------------- |
| Enable Noise Cancelling | L2CAP Send    | 0x000B | 32     | 09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C |
|                         |               |        |        | 0100 0000 0768 1701 0100 0014 A93C 2540 |
|                         | L2CAP Receive |        | 14     | 0BEF 1200 FF5A 0009 40DF DA00 A59A      |
| ASC Off                 | L2CAP Send    | 0x000B | 32     | 09EF 39FF 5A00 1C40 ---- ---- ---- 3E0C |
|                         |               |        |        | 0000 0000 0768 1701 0000 0014 A73C 2740 |