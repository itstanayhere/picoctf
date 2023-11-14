Keygenme-py

We download the given python script:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/e735433c-dc2c-4602-ab30-1d0d73e5da8c)
 

This is what it looks like:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/ddde6c30-37e5-40c7-a5b8-9b02ee3b94e9)

 
 (an ss of the script from VSCode)

To run the program, we first need to install the cryptography package.

We do so using the pip install command.

pip is a package manager for python that allows us to import specific packages or modules into our code. A module can be thought of as a function in a program while a package can be thought as a collection of modules.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/06d5a728-ed09-47f0-b603-107c757a695a)
 
Now the cryptography package is installed.

I ran the program, and it displayed various options. Testing each one did not give any meaningful output.

For option (a)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/65c41806-901c-4202-9f50-62bc5eb23cb9)


Option (b)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/c32ffdb2-0e0e-466c-b87c-86b368fbc270)
 

Option (c):

![image](https://github.com/itstanayhere/picoctf/assets/147296398/4a17438e-ab50-45ce-8e2b-cd82b083a866)


Option (d) caused me to exit the output. (as expected)

My first line of thought was that there must be a licence key hidden somewhere in the script, which would enable me to access option (b). So I tried looking for it, but it was a false lead.

As it turned out, I did not need a licence key. This clicked when I looked closely at the start of the code.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/ed4be220-4006-46c0-b5bc-07a2cebbe722)


As we see, the flag is made of 3 parts. It is the second part, ‘key_part_dynamic1_trial’ that we need to determine to complete the flag.

Further down in the program:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/fa46323b-1f02-42d3-862c-d83c67b75b74)


The for loop is meant to increment the value of ‘i’ , which is clearly indicating the index of a certain character in the key. 

There are also several if-else conditions that follow, which are comparing the values of the character at the ‘i’ th index of the key to the actual key that must be the flag.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/59eed599-8c48-4bdb-8866-aae00445d457)

 

So we can now reverse engineer the characters from these conditions.

We see the following code in each condition:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/7b209705-1e52-4e0e-9a0a-fe1eef6aecb6)
 

Here is the meaning of the various terms involved in this line:

hashlib: It is a library containing various hash functions to form the hash (non-decryptable form) of plaintext.

sha256(<bstring>): This produces a 256 bit hash of the binary string passed as a function to it. It uses 32 bit words. sha performs various mathematical operations on a bytes string, making it practically impossible to brute-force it back to plaintext. It is part of the SHA-2 family.

hexdigest(): It converts a hash digest into a hexadecimal string. It consists of characters from 0-9 and A to F. 

In our case, the value of username_trial is “FRASER”, which we are supposed to pass as a bytes string to the above function. A byte string is a string that isn’t human readable. For example, an image when stored as a .jpg file is encoded in a certain manner and stored in the memory of the computer. Similarly, the system stores this string in such a manner.

We now use the same function in a different program to get the characters one by one.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/7534c4b5-b61a-4618-9869-3bad97c12de2)


The characters we need are at the [<integer>] index.
Here is the code we will be using to decode.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/ab1400a3-a5cf-4eea-b586-fd9fd9f6e09f)


We need the characters at indices: 4,5,3,6,2,7,1,8

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/44d63615-3309-4c11-9176-33f9c13a6c78)


Characters are:

ac73dc29

This completes our flag:

picoCTF{1n_7h3_|<3y_of_ac73dc29}

Upon passing this, 

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/b7a3327f-88d8-4d9e-9c0a-ccfa2bb3af94)


This completes this level.
