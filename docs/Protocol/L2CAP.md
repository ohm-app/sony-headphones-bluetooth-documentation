# L2CAP

L2CAP is a lower-layer protcol than [RFCOMM](RFCOMM.md). It is used to send [RFCOMM](RFCOMM.md) frames over Bluetooth.
When capturing Bluetooth packets, you might encounter L2CAP packets instead of pure [RFCOMM](RFCOMM.md) packets.

Understanding what the entire L2CAP frame looks like is not necessary to understand captured Bluetooth packets.
However, roughly knowing what you're looking at and knowing what the actual Data payload is can be helpful.

## L2CAP Frame

Let's compare an L2CAP frame to an [RFCOMM](RFCOMM.md) frame:

| L2CAP Frame                                                                         | [RFCOMM](RFCOMM.md) frame                                                 |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| 09EF 39**FF 5A00 1C40 890D EACB 0022 ЗEОС 0100 0000 0768 1701 0100 0014 A93C 12**40 | **FF5A 001C 4089 0DEA CB00 223E 0C01 0000 0007 6817 0101 0000 14A9 3C12** |

The bold parts are the parts that are the same in both frames. The rest is L2CAP specific.

!!! note
    The first Word in the L2CAP Frame (`09EF`) contains information about the [RFCOMM](RFCOMM.md) Address and Control Bits.
    `09` being the Address, and `EF` being the Control Bits. 
