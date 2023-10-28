# Specification

The protocol uses RFCOMM-like protocols on top of L2CAP to communicate over Bluetooth.

!!!note
    The protocol used here seems to be a custom protocol, built on RFCOMM.

The packages consist of a header, a data section and a Frame Check Sequence (FCS).

| Position in Bits | Name                       |
| ---------------- | -------------------------- |
| 1-8              | Address                    |
| 9-16             | Control                    |
| 17-40            | ???                        |
| 25-32            | Length                     |
|                  | Data (0 - 32767 Bytes)     |
| Last 8 Bits      | Frame Check Sequence (FCS) |

!!!note
    "8 bit" means eight binary numbers. 4 binary numbers are equivalent to 1 hexadecimal number, so 8 bit are 2 hexadecimal digits.

Looking at an examplary Data Capture, we can see which part of the frame is what:

```
09EF 39FF 5A00 1C40 F019 EA58 0024 3E0C
0000 0000 0768 1701 0100 0014 A83C 1240 
```

| Data (Hex)                                                     | RFCOMM Frame Part                                                                                             |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `09`                                                           | Address (`0x09` in binary is `0000 1001`, signaling 2 Address fields. See: [Extend Address Field](#ea-field)) |
| `EF`                                                           | Control                                                                                                       |
| `39FF 5A`                                                      | ??? "Weird Bytes"                                                                                             |
| `001C`                                                         | Length                                                                                                        |
| `40 F019 EA58 0024 3E0C 0000 0000 0768 1701 0100 0014 A83C 12` | Data                                                                                                          |
| `40`                                                           | FCS                                                                                                           |

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

## Reference
- RFCOMM Spec: <https://web.archive.org/web/20231022193147/https://ptgmedia.pearsoncmg.com/imprint_downloads/informit/bookreg/9780130661067/cr_ch10.pdf>