Babygame01: (The instance I solved it in is different from the one shown in the write-up)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/b851a540-7bf8-4d6f-ba12-8f6b6d430179)

 
We launch an instance (a particular case of a said class)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/2e521a8a-ede3-404d-bb8c-017032d11b23)

 
We connect with the game using the command given.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/fbc306e2-3045-4322-b867-93aefc35dca6)


Following is the output:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/81b638e3-1ee0-4664-804f-6411c44db6c7)
 

Opening the source code of the game in ghidra as a decompiler (ghidra is a reverse engineering software made by the NSA [National Security Agency, USA]).

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/2c29293e-b195-483c-a9d1-b60c5318a15e)


We see that the p command solves the game at once, as opposed to the other commands that just move us around.

The solve_round function:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/883ab9e8-efe6-4bf6-9daa-ac5dec8a7e10)


As we see, the parameters must match the given ones for the game to be solved.

Upon typing p as a command,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/ff049119-c2af-49de-addf-79f923aa9d82)


The output is:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/09cab16f-fd86-4111-80cb-e944eb874b1e)


We won the game but don’t have any flag.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/14d5264c-0622-4d26-ad8c-a14b8db9b6ba)
 

We see that the flag can only be obtained if we local_aa4 is not a null character.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/d893aea3-c70f-41c0-842a-ac3a6dbf7464)
 

We see that local_aa8 and local_aa4 are in the same stack. 

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/0a3aa763-7c85-4501-bee4-51fb65205bc9)


And the memory location of local_aa8 is greater than that of local_aa4. This means that upon moving 4 bytes backward in the memory location, out character ‘@’ will be reach local_aa4, fulfilling the condition for the flag to be printed.

Upon doing this,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/f49c268b-142e-444b-80ed-859423896615)

'Player has flag: 64' means that local_aa4 now stores the ASCII value of 64, which is nothing but the '@' symbol. which is what we needed

Now I typed in ‘p’ command to solve the puzzle,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/fb7e5f63-a274-4310-a498-c8075b131c38)

This is our needed flag.
