ARMAssembly 0:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/c6767f96-2eeb-4d7c-8337-ac595d8e8ed1)


Its given as a hint that we simply have to compare the hexadecimal forms of the given numbers, which we can get easily by running a python script.

I converted the first integer to hex:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/edf0703b-72cd-428d-8770-d00ac1925984)

Output:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/45875099-f357-41e6-995b-95d524907ed9)


When I passed this as an argument in the picoCTF{}, it returned the flag as incorrect. So I tried the next integer.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/feae1f53-f194-41bb-a105-c427f3e77e57)


Output:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/ea868ef3-0cf0-4737-8c7a-2948771c0a32)


When I passed the following:

picoCTF{5ee79c2b} as the flag,
 
![image](https://github.com/itstanayhere/picoctf/assets/147296398/4615e960-6df7-4d64-aef8-fe09bebf5e3b)

[I could not understand the assembly language code, so I tried this to see if I could cross the level]

This completes this level. 
