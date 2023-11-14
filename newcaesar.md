new caesar:

Following is the encoding part of the source code:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/8ca61727-e7d1-42d3-83d6-c00f7a72c73f)


Upon passing some random values:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/9ef2e210-d747-4696-960d-9d6f863582ae)

 
We get:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/22274b4f-83db-4ee1-85c3-5c94830267fb)


What happens in the encoding is as follows:

The ascii of ‘a’ is 97, and its binary is:
 
 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/f9627661-f1a1-4a2d-af37-acf110418601)


The binary is being split in pairs of 4, in this case:

0110 and 0001, which have the equivalent of 6 and 1. 

Now ‘g’ is at the 6th index of ALPHABET. Similarly ‘b’ is at the first index of ALPHABET. Here ALPHABET consists of all alphabets from a to p.

Therefore a=gb

As for the shift function, we just pass on each character of the encoded string and every character in ALPHABET.

This way we can obtain every possible decryption and pick out the one best fit for the flag.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/d6ec8f5d-6a86-40fa-ad64-046209aa3c17)


This is the decoding snippet.

Running it,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/28cc924f-78e5-4347-9474-84323b324203)


Of all these, only the one with key= ‘d’ consists of all human readable characters. So that is our flag.
