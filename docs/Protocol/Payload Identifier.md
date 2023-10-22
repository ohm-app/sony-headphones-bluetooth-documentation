# Payload Identifier

!!! example "Information"
    The information on this page is incomplete.

Requests issued by the official client have some sort of payload identifier.
It has been observed that requests with length 25-32 bytes send this payload identifier.

Let's look at an example, Base16 encoded L2CAP Payload:

```
09EF 2BFF 5A00 15F0 01C3 EAA4 0015 3E01
```

The fourth-to-last byte and third-to-last byte (`01C3 EAA4`) are the payload identifier.
The first payload identifier byte is split into two smaller bytes, `01` and `C3`, giving us `01 C3 EAA4` as the payload identifier.

## Calculating the Payload Identifier

!!! bug "Investigation needed"
    This entire section needs to be reworked. Apparently, the payload identifier is not quite calculated as described here.

The starting value for the payload identifier is yet unknown.
However, the pattern for calculating the payload identifier for the next request $Y$ is known, given a previous payload identifier $X$.

For easier understanding, let's split our payload identifier 

$X$ = `01 C3 EAA4`

into

$X_1$ = `01`, $X_2$ = `C3` and $X_3$ = `EAA4`.

The payload identifier for the next request $Y$ is calculated as follows:
$Y = (X_1 + 1) \circ (X_2 + 1) \circ (X_3 - 2)$

where $\circ$ is the [concatenation](https://en.wikipedia.org/wiki/Concatenation) operator.

This means, $Y$ would equal `02C4 EAA2` in our example.