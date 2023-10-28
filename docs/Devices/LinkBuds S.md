# Sony LinkBuds S

## Commands

!!! warning
    The data here is not yet fully understood. This simply what we know at the moment. Use this information at your own risk.

!!! info
    RFCOMM over L2CAP is used for communication between the LinkBuds S and the host device. If you
    are capturing Bluetooth packets, you will see the full RFCOMM data, not just the data payload.
    Read more about the [data structure](../Protocol/Specification.md) of RFCOMM frames.

The tables below show the data packets sent and received for performing a given action.

### Ambient Sound Control (AmSC)

!!! note
    The italicized text in the tables below is data which is inconsistent between packets. Until this data is understood, it is being referred to as "Weird Bytes" and might as well be random. 

| Action                    | Type | "Weird Bytes" | "RFCOMM Data" Payload                                                          |
| ------------------------- | ---- | ------------- | ------------------------------------------------------------------------------ |
| Ambient Sound Control Off | Send | 39FF 5A       | **40** *BEDE EAC5 0027* **3E0C 0000 0000 0768 1701 0000 0008** *9B3C 29***40** |
| Noise Cancelling On       | Send | 39FF 5A       | **40** *ECE1 EA44 0029* **3E0C 0100 0000 0768 1701 0100 0008** *9D3C 23***40** |
| Ambient Sound: 1          | Send | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0001** *963C 31***40** |
| Ambient Sound: 2          | Send | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0002** *983C 31***40** |
| Ambient Sound: 3          | Send | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0003** *983C 31***40** |

!!! note "Ambient Sound Levels"
    Ambient Sound levels go up to 20. To represent the values 4 to 20, set the bytes which were 0001, 0002 and 0003 for levels 1 to 3 respectively
    to the desired level in hexadecimal. For example, to set the level to 4, set the bytes to 0004. To set the level to 20, set the bytes to 0014.