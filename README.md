# 32bitARM_like_CPU_design
This repository contains the complete source code, design files, and course materials for designing an ARM-like CPU, which have designed during our recorded workshop named : Build CPU from SCRATCH with verilog. hosted in www.whyrd.in . The project focuses on educational purposes, teaching the principles of RISC-based microarchitecture, memory management, and instruction decoding.

Full workshop link: https://whyrd.graphy.com/courses/Build-CPU-from-SCRATCH-with-Verilog-66d32e96efbca47d4b9bcf47 

Course Thumbnail : 
![image](https://github.com/user-attachments/assets/0a885f87-6974-49f1-b9fb-4b30cf79d880)


## CPUs Instruction set 
Our designed CPU can handle the following commands. 

Data Processing: ADD SUB AND ORR 

Memory Operation: STR and LDR 

Branch: B 

Also, cover all the conditional mnemonics from ARM LRM, as shown in the snapshot below. 

![WhatsApp Image 2024-10-21 at 8 50 46 PM](https://github.com/user-attachments/assets/5dfd10a9-aad9-4771-a08e-51e941b20dde)
ref: Digital Design and Computer Architecture ARM edition by Harris


## Micro Architecture top view (rough) : 
![image](https://github.com/user-attachments/assets/f37b1b66-d345-4d15-9b75-08f2a79659e7)


## Micro Architecture in details : 

In our workshop, we have explained the reason behind each line of wire across multiple episodes. 

![image](https://github.com/user-attachments/assets/0cbcf160-2750-4286-9c24-b48418b063c9)

## More into the controller 

![image](https://github.com/user-attachments/assets/d0f56724-bb97-469b-aa8c-ea7331d043e2)


### Decoders : 

![image](https://github.com/user-attachments/assets/a8027633-5732-4f60-b408-e2e7966c2525)


## How verilog modules are being integrated : 

![image](https://github.com/user-attachments/assets/6b6fbceb-fa39-4612-9ccd-498138879169)



You can see Data memory and instruction memory are not part of the core CPU, the core CPU consists of a controller and datapath 

datapath.v : This instantiates the following module 

![image](https://github.com/user-attachments/assets/1b67d459-65a1-49ab-8c15-b5fc1e62d43a)

controller.v : This instantiates the following module 

![image](https://github.com/user-attachments/assets/ccd0bed5-1f29-407e-bafc-6e9bf7bafbaa)


cpu.v : instantiate both datapath.v and contoller.v 


top.v : Integrate cpu.v and imem.v and dmem.v 



## Testing : 

To test a CPU working we need to have an extensive code which can examine each and every instruction covered in this CPU design , and then if that code is being executed by our CPU 
with the required final result we can say that CPU passed the initial test 

To test our design, we have taken reference test Code from Digital Design and Computer Architecture ARM edition by Harris. 

### Test Code : 

![image](https://github.com/user-attachments/assets/6597a10c-7191-4b00-bbf0-d3e907aeeedd)


imem.v : instruction memory source this codes in hexadecimal format . 

testbench.sv : Check if we are getting mem[84]==7 or not, which is the final expected outcome of this test code . 


### Additionally we can test each block separately in isolation: 

aluTest.v : testbench for ALu block 

testbench for other block will be loaded in few days . 
























