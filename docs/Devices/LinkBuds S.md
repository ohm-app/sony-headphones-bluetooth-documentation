# Sony LinkBuds S

## Commands

!!! warning
    The data here is not yet fully understood. This simply what we know at the moment. Use this information at your own risk.

!!! info "Info: About the Protocol"
    RFCOMM over L2CAP is used for communication between the LinkBuds S and the host device. If you
    are capturing Bluetooth packets, you will see the full RFCOMM data, not just the data payload.
    Read more about the [data structure](../Protocol/Specification.md) of RFCOMM frames.

!!! note
    The italicized text in the tables below is data which is inconsistent between packets. Until this data is understood, it is being referred to as "Weird Bytes" and might as well be random.

!!! note
    The "RFCOMM Data" does not include the Address-, Control-, Length- and FCS-Bytes of the RFCOMM frame. It only includes the data payload.

The tables below show the data packets sent for performing a given action.

### Ambient Sound Control (AmSC)


| Action                    | Length (L2CAP) | "Weird Bytes" | "RFCOMM Data" Payload                                                    |
| ------------------------- | -------------- | ------------- | ------------------------------------------------------------------------ |
| Ambient Sound Control Off | 32             | 39FF 5A       | **40** *BEDE EAC5 0027* **3E0C 0000 0000 0768 1701 0000 0008** *9B3C 29* |
| Noise Cancelling On       | 32             | 39FF 5A       | **40** *ECE1 EA44 0029* **3E0C 0100 0000 0768 1701 0100 0008** *9D3C 23* |
| Ambient Sound: 1          | 32             | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0001** *963C 31* |
| Ambient Sound: 2          | 32             | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0002** *983C 31* |
| Ambient Sound: 3          | 32             | 39FF 5A       | **40** *6005 EAFC 0029* **3E0C 0000 0000 0768 1701 0101 0003** *983C 31* |

### Speak to Chat

| Action     | Length (L2CAP) | "Weird Bytes" | "RFCOMM Data" Payload                         |
| ---------- | -------------- | ------------- | --------------------------------------------- |
| Toggle On  | 29             | 33FF 5A       | **40** *AAE1 EAD9* **002A 0100 0000 04F8 0C00 0116 3C** |
| Toggle Off | 29             | 33FF 5A       | **40** *AEE5 EAD1* **002A 0000 0000 04F8 0C01 0116 3C** |

!!! note "Ambient Sound Levels"
    Ambient Sound levels go up to 20. To represent the values 4 to 20, set the bytes which were 0x0001, 0x0002 and 0x0003 for levels 1 to 3 respectively
    to the desired level in hexadecimal. For example, to set the level to 4, set the bytes to 0x0004. To set the level to 20, set the bytes to 0x0014, etc..
    