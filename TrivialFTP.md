Trivial FTP:

The question is as follows:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/864898bb-87c7-4c18-9abb-16409a1a4677)


A wireshark capture file is downloaded.

I opened this using wireshark (a packet sniffing software)
![image](https://github.com/itstanayhere/picoctf/assets/147296398/45617412-21b4-4f16-a47a-0baa94ca7504)

 

There are many tftp protocols here. tftp stands for trivial file transfer protocol. Its similar to http(using tcp to communicate information with other pages,browsers etc.) and other transfer protocols.

Wireshark can export tftp objects, enabling us to store the actual files being transferred. Since the flag is the file being transferred as per the question, we export the objects

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/e645fd14-ac23-4c8e-a00b-d27b0a1e1b0d)


I stored these in a file ‘ws’

Viewing contents,

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/df47b8ff-6c72-4074-93dd-aca24347e8b3)


Note that this contains a .deb file, meaning we have to use a linux environment. So I copied the same folder onto a VM.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/20e4461f-688b-46b4-b865-eedc2e176c69)


Following are the contents:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/994e02a9-e3ca-4b9a-a760-3e26660ee540)


instructions.txt:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/e85c1eed-bd9c-4356-9780-7da0d4efcad6)


plan:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/d568fac4-eea0-4a7e-8322-5a489508b47f)


I changed my cwd to ws as that is where all the files are.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/9240ee25-f53e-4cdb-a5b9-7ef45767224e)


Both of these are ciphered in ROT13 at first glance. So I ran a check and:

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/20fb3a10-3680-47b0-8738-009c1f9af981)

![image](https://github.com/itstanayhere/picoctf/assets/147296398/e202099f-4249-42fc-a101-e4a33b976e22)

 

The program.deb file was to install the steghide package, but since the VM could not install it from the file, I installed it in the terminal instead.

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/6186f7b8-7846-4eec-b79d-b3cebb59e050)


With steghide now installed, I could take a look at the pictures for the flag. (steghide is a tool used to hide data inside of bmp,jpg, au and wav files. It is mostly used in Kali Linux)

After some reading online, I figured out how to extract data from files using steghide. The command is:

steghide extract -sf [file]

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/78b62e68-2df2-4248-9d1a-94495fd56b6a)


The passphrase is DUEDILIGENCE (as mentioned in plan.txt)

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/65ce5e0f-c2f3-438f-9797-adc8cb137349)


So there is no relevant data to us in picture1.bmp

Same is the case with picture2.bmp

 ![image](https://github.com/itstanayhere/picoctf/assets/147296398/48964db6-3e4d-49ca-bdfa-40e0df897d44)


But in picture3.bmp :

![image](https://github.com/itstanayhere/picoctf/assets/147296398/32fff44a-b1f9-43b8-a44c-bca7a02e02a7)
 

So the flag is stored in flag.txt . All we have to do is simply display its contents.

![image](https://github.com/itstanayhere/picoctf/assets/147296398/0dce2c4d-b6e8-4d00-9aa5-38219ba6fabc)

This is our flag.
