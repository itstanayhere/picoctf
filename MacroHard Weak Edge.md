MacroHard WeakEdge

The following is the question:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/0b07212e-e047-4c83-a6fa-2b5fd1514b94)


It’s a pptm file that contains the flag. 

pptx:
It does not contain macros, so is less vulnerable to security risks	
pptm:
Contains macros which makes it more vulnerable to security risks
(source: LifeWire)

A macro is a small piece of code that automates certain tasks. It is an efficient tool but poses a security risk as they are imported from across the web and may contain malicious code.

I initially opened the pptm file, but it was simply a blank ppt. There was nothing to be found even in the properties of the file.
After some reading about pptx and pptm online, I found that both these files are essentially zipped files. 
Since it is a pptm file, not in a bz2 or gz format, none of the tools we learnt about in Bandit will help. Therefore I used the unzip command.

unzip command is a powerful command in linux that can easily unzip and extract zipped files.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/ce667c7d-15fb-4920-b077-185a06bc4398)


Since we need to store the extracted files somewhere, I created a directory ‘pico’ for the purpose.


Following is the output:



![image](https://github.com/itstanayhere/picoctf/assets/147296398/d1f516ae-024d-46ae-a8fa-391995290f65)


 

We see a file ‘hidden’. This must contain the flag. So we change the cwd to that.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/266bf0d2-988c-430a-940c-40306adc08d1)
 

Now we display the contents of ‘hidden’

![image](https://github.com/itstanayhere/picoctf/assets/147296398/7679093d-23cf-45e3-866f-c1019684db08)
 

These characters appear to be encoded in base64.

Decoding them, we get:
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}

This is our needed flag
