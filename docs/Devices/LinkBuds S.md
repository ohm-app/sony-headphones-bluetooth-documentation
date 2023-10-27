# Sony LinkBuds S

## Commands

!!! failure
    This entire document is being remade. Please check back later.

!!! info
    RFCOMM over L2CAP is used for communication between the LinkBuds S and the host device. If you
    are capturing Bluetooth packets, you will see the full RFCOMM data, not just the data payload.
    Read more about the [data structure](../Protocol/Data%20Structure.md) of RFCOMM frames.

The tables below show the packets sent and received for performing a given action.
The tables are ordered by the time the Bluetooth messages were sent or received, with the first message at the top.

### Ambient Sound Control (AmSC)

| Action                  | Type          | "RFCOMM Data" Payload                   |
| ----------------------- | ------------- | --------------------------------------- |
| 