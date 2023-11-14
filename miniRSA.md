miniRSA

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/78c918a8-1911-4136-aeb4-adf5f4f8bcc0)


The following is our ciphertext:

2205316413931134031074603746928247799030155221252519872650073010782049179856976080512716237308882294226369300412719995904064931819531456392957957122459640736424089744772221933500860936331459280832211445548332429338572369823704784625368933 

And the value of e is given to be 3.

In the wiki page:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/f5dd2b47-54bc-46d3-ba46-4e11673db99f)
 

We observe that (mod n) remains in ciphered and deciphered text. So essentially we have to calculate the e-th root of ‘c’ to get our message.

That is what we do.

The cube root (e=3) of ciphertext is:

13016382529449106065894479374027604750406953699090365388203708028670029596145277

(I had to use an online calculator for this as python was not returning the exact answer)

I converted it to hex. This was what was returned:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/e3031e58-2272-4562-bf10-b979be2e6bc4)


Upon converting this to ASCII:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/b78e984c-8c70-4d8d-b32a-47063c2fbb17)


This is our flag
