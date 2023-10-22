# Data Structure

The protocol uses the L2CAP and RFCOMM protocols to communicate over Bluetooth. Understanding how an
RFCOMM frame is structured is important to understand captured Bluetooth packets.

## RFCOMM Frame

An RFCOMM frame consists of a header, a data section and a Frame Check Sequence (FCS).

| Position in Bits | Name                       |
| ---------------- | -------------------------- |
| 0-7              | Address                    |
| 8-15             | Control                    |
| 16-23            | Length                     |
| 24-31            | Length or Data             |
|                  | Data (0 - 32767 Bytes)     |
| Last 8 Bits      | Frame Check Sequence (FCS) |

Looking at an examplary RFCOMM frame, we can see which part of the frame is what:

```
F3EF 39FF 5A00 1C40 04E0 EA7D 001E 3E0C
0000 0000 0768 1701 0100 0014 A83C 18B3
```

!!!note
    "8 bit" means eight binary numbers. 2 binary numbers are equivalent to 1 hexadecimal number, so 8 bit are 4 hexadecimal numbers.

| Data (Hex)                                               | RFCOMM Frame Part                                                                                                     |
| -------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `F3E4`                                                   | Address (The first bit of `F3E4` is 1, meaning there is only one address octet. See: [Extend Address Field](#ea-field))  |
| `39FF`                                                   | Control                                                                                                               |
| `5A00`                                                   | Length                                                                                                                |
| `1C40`                                                   | Length or Data (The first bit of `5A00` is 0, meaning this is a length field. See: [Extend Address Field](#ea-field)) |
| `04E0 EA7d 001E 3E0C 0000 0000 0768 1701 0100 0014 A83C` | Data                                                                                                                  |
| `18B3`                                                   | FCS                                                                                                                   |

## <a name="ea-field"></a>Extend Address Field

The Extend Address (EA) field can extend the *address* or *length* fields. To calculate whether the
fields will be extended by 8 more bits or not, we need to convert the field from hexadecimal to
binary.

`F3E4` (Base16) = `1111001111100100`(Base2)

The first bit is the *EA bit*. If it is set to 0, then extension will occur. If it is set to 1, then
no extension will occur.

### Extension of Fields

**Address Field**

If EA=0 for the address fields, then more address octets will follow. If EA=1, then the field we are
looking at is the last address octet.

**Length Field**

If EA=0 for the length field, then the EA bit will be followed by 15 bits of length. If EA=1, then
only 7 bits of length will follow.