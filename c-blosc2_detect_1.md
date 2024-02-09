Affected Version:
c-blosc2 2.13.2 fd6ec1fb17f9b93938e907bd57b07858902df969

Vulnerability Description:
The vulnerability is a memory leak bug located at line 565 of the file /c-blosc2/blosc/schunk.c. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

c-blosc2 download address:
https://github.com/Blosc/c-blosc2.git

1.In the file /c-blosc2/blosc/schunk.c, a pointer named "frame" is defined at line 557, and a block of dynamic memory space is allocated for this pointer using the function frame_from_cframe, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/c-blosc2_defects/blob/main/c-blosc2_1.png)

2.At line 883 of the frame_from_cframe function, the calloc function is used to allocate a block of dynamic memory space for the pointer variable "frame," and at line 907, the pointer "frame" is returned, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/c-blosc2_defects/blob/main/c-blosc2_2.png)

3.When the condition of the if statement at line 564 evaluates to true, the program returns NULL at line 565 without releasing the dynamic memory region pointed to by the pointer "frame," thus constituting a memory leak defect, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/c-blosc2_defects/blob/main/c-blosc2_3.png)
