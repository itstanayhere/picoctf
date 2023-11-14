GDB Baby Step 1:

The following is the question:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/9ea9b3de-6b8b-46c2-b905-bfbf8bb01b83)


Upon viewing the hints, it is essential that gdb (a portable debugger that supports many languages and is designed for Unix based systems) is to be used to find the bugs in the needed code.

We download the file and then open the terminal.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/2de3f8d8-8c2c-4e8f-a9d3-90f6fdf95de3)


We install gdb using command:

sudo apt install gdb

sudo 	Short for “super user do”. There are many functions a normal user is not allowed to perform and it is not always safe to be operating as the root user. So we use the sudo command to perform some functions we wouldn’t be able to do normally.
apt 	Short for “Advanced Package Tool”, a software that helps us to install, remove and update packages on Debian(open source computer OS system) based OS such as Ubuntu
install 	A simple install command which will install the package we specify ahead of it
gdb 	The package we want to install at present

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/e359a605-baa3-4175-96b9-989e566667d4)


To enter gdb, we simply type ‘gdb’ in the terminal:

![image](https://github.com/itstanayhere/picoctf/assets/147296398/35193409-4bcd-4957-9e84-558b1bd86826)

 

Since we need to view the flow of the program in order to find our flag, this is what we do:

The file command looks for bugs in our file while simultaneously executing it, and returns the bugs (if any). So we run the ‘file’ command.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/e048e284-a9de-44ed-b0e6-4cb2d3b374e1)


It shows us that no debugging symbols(They map instructions in the compiled binary program to their corresponding variable, function, or line in the source code) were found.

After some reading online, I found that every code is broken down to assembly language first. So I decided to switch to ASM environment in gdb.

To do so I used the ‘layout asm’ command,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/368d38bb-1f9f-4690-a641-2827ef1a15ad)


This is the screen displayed:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/071d8514-59b1-4b89-ae6f-9c67f3be2d8a)


Of this, we see 

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/fe2beab2-e3c8-4889-b91d-511ab8787d07)


0x1138	This is the memory address where the instruction is located. It is in hexadecimal form.
<main+15>	This indicates that the instruction is 15 bytes offset from the start of a function named main. The main function is usually the entry point for execution in most programs.
mov	"mov" is a commonly used x86 Assembly instruction that copies data from one location to another.
0x86342	This represents an immediate value (a constant number) in hexadecimal that is to be moved into the destination operand.
%eax	This is the destination operand, which in this case is the eax register.

In a nutshell,  at the memory address 0x1138, which is 15 bytes into the main function, there is an instruction (mov) that moves the hexadecimal constant 0x86342 into the eax register.

This matches our needed format.

So 0x86342 is our needed flag.

Converting it into the needed form:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/96922b04-c1ce-4785-ad36-c874f69fc255)


Our flag is:

picoCTF{549698}

Passing this into picoCTF:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/9a761f7c-9a7c-40a9-a1e3-8063719cd982)


This completes this domain’s assigned challenges

[Sources: GeeksForGeeks, StackOverflow, SuperUser, AppleDev, Google, sourceware.org, inbuilt gdb suggestions]
