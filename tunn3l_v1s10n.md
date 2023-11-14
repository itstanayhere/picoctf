tun3l v1s10n:

A bmp file is downloaded from the picoCTF page.
![image](https://github.com/itstanayhere/picoctf/assets/147296398/752520b8-6261-4c66-a030-1a31b3a067ad)

 
![image](https://github.com/itstanayhere/picoctf/assets/147296398/000fd7e5-f48d-45b4-a4a6-d612717a1295)

 

So we have to adjust the size of a bmp image. This can be done by altering the hexdump of said file.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/104c4883-f8b9-44db-9df4-dd2649b50ce0)


Upon comparing this to a standard bmp file, I found that 

![image](https://github.com/itstanayhere/picoctf/assets/147296398/3417209b-e471-417e-a2a1-90db66ad0b96)
 

Are supposed to have static values. So I changed them.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/efaf2c4a-b4d3-4eb4-9d01-eb5858169fcb)


This is what I got:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/b30c4bb4-f290-44b9-b01d-1dd29426c033)



So there is something more hidden in the image.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/a0f90287-09e8-4f51-a10e-6eed6c824dfe)


Let us try extending the height, as it is too less in comparison with the width and might contain some extra clues.

The maximum permissible height in 32K pixels for a bmp image (source:stackoverflow). I tried 2000 pixels at first. This made the image too big to view anything. Same with 1000 pixels. But when I tried it out with 850 pixels.

I did this by converting the pixel lengths into their equivalent hexadecimal values and replacing them in the hexdump by comparing with hexdump of a standard file.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/27c756b0-7176-43e1-ac69-88c0b0e682a3)
 

We have our flag.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/22b56e44-3d4a-4fab-a369-54af65abe0c7)


(t1,t2,t3 are the file with height 2000,1000,900 pixels respectively)
