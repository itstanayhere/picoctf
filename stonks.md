stonks (attempted but not accepting flag)

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/c9a11bda-4c4f-4f58-97c2-bcb93d6d96ff)


I ran the nc command in linux terminal:
![image](https://github.com/itstanayhere/picoctf/assets/147296398/23b16fbc-075b-4781-a696-0486eb804d90)
 

Since the vulnerability is in the API key,I picked option 1 (as per the code provided, API can only be accessed through this method)

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/fe04a622-56ae-48d9-82b5-de32debbad48)


It is asking us for an API token. 

In programs, local variables and other data are stored in stacks,buffers and other data structures, and passing a large input can cause them to overflow. We will exploit this by passing a large number format specifiers into the input, as this will cause the code to read out of bounds data, which might contain the flag.

I tried doing this using %c but there were too many non-printable characters, making reading the flag difficult. So I passed %X instead. This returned appropriate hex values. Also since the length is specified as less than 300, we have an estimate of how many to pass

I passed 120 such %X, following was the output:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/4672149d-bcdb-43a3-a46b-96175eaa8134)


Converting this hex to ascii text, we can clearly see a hidden flag:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/965b6691-5ae3-4c02-b32f-39c554e0b0d6)


I converted this scrambled flag to a proper one manually:
 
![image](https://github.com/itstanayhere/picoctf/assets/147296398/fce36119-5ac5-428e-b86f-a0fbd5774d5e)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/becdf3b7-dd88-450e-a508-12c347add1cc)

However this flag was not being accepted, even after I tried other combinations with the various pieces of characters. It is correct to my understanding.
