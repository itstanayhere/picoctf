buffer overflow 0

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/c618a874-ffd0-47ff-b880-b6539a194f91)


As the question suggests, we have to cause a stack overflow. So, we use the same trick as in ‘stonks’.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/3d4dcc85-b070-4b67-b623-89dc5441864a)


Its clear from the source code that we have to pass a large number of characters. That’s what we do.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/a0a40278-5456-41f0-98c7-5b16fc501a10)


We have our flag.
