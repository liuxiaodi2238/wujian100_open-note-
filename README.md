# wujian100_open 
wujian100_open is a MCU base SoC. 
开源的无剑100是一个基于SOC的MCU（单片机）。
We can simulate by EDA tools and emulate by FPGA. 
我们可以通过EDA工具模拟，通过FPGA进行仿真。
Also we can develop the IPs and software in this platform. 
我们也可以在这个平台里开发ip和软件。
We wish more and more developers building the open MCU ecosystem with T-Head. 
我们希望越来越多的开发者和T-head一起构建开源MCU生态。
IC design and development should be faster simpler and more reliable
（促使）集成电路的设计和开发更快更稳定可靠。
    
    Directory Structure   文件结构
    |--Project                //open source project work directory  
      |--riscv_toolchain      //tool chain install directory download from t-head.cn
      |--wujian100_open       //wujian100_open project get from github
        |--case               //test case example for simulation
        |--doc                //wujian100_open user guide
        |--fpga               //FPGA script
        |--lib                //compile script for simulation
        |--regress            //regression result
        |--sdk                //software design kit
        |--soc                //Soc RTL source code
        |--tb                 //test bench
        |--tools              //simulation script and setup file
        |--workdir            //simulation directory
        |--LICENSE
        |--README.md
# Get Start
    1. prepare a project work directory just like 'Project'
    2. cd Project
    3. git clone https://github.com/T-head-Semi/wujian100_open.git or git clone git@github.com:T-head-Semi/wujian100_open.git
# Download C/C++ Compiler
    1. prepare a tool chain install directory named 'riscv_toolchain'  // use the c shell command like 'mkdir riscv_toolchain'
    2. download the tool chain from the url https://www.t-head.cn/product/mcu-platform?spm=a2ouz.12987052.0.0.167548abiiSAQs
    3. install the tool chain to the riscv_toolchain dirctory
# Get ready for simulation
    1. cd wujian100_open/tools
    2. vim setup.csh then add the vcs path and license
    3. source setup.csh         //if not success you can touch a new file named setup.csh and copy the content to the new file. then source the new file
    4. chmod 777 run_case Src2vmem
    5. cd wujian100_open/workdir
    6. execute the command '../tools/run_case ../case/timer/timer_test.c'
# Get ready for FPGA bit generation
    1. make sure you have the synplify and license
    2. cd wujian100_open/fpga/synplify
    3. execute the synplify and load the wujian100_open_200t_3b.prj file
    4. input the command 'sdc2fdc' in synplify
    5. start the synplify
    6. after synplify generated the netlist we will use vivado for P&R and generated the bit file
    7. make sure you have the vivado and licese
    8. cd wujian100_open/fpga/vivado
    9. run tcl use file 'wujian100_open_200t_3b_prj.tcl'
    10. program the bit file to the fpga board
    11. enjoy the application development
# How to get the FPGA
#如何获得FPGA
    apply from the url https://www.t-head.cn/product/mcu-platform?spm=a2ouz.12987052.0.0.167548abiiSAQs
# How to get the debug tool
#如何获得debug工具
    download from the url https://www.t-head.cn/product/mcu-platform?spm=a2ouz.12987052.0.0.167548abiiSAQs 
# How to get the IDE for development
#如何为开发准备集成开发环境    IDE：集成开发环境
    download from the url https://www.t-head.cn/product/mcu-platform?spm=a2ouz.12987052.0.0.167548abiiSAQs  
# How to use the sdk
#如何使用软件开发工具包    sdk：软件开发工具包
wujian100_open SDK is wujian100_open software development kit, the software follows the CSI interface specification. Through the SDK users can quickly wujian100_open test and evaluation. At the same time users can refer to the SDK integration of various commonly used components and sample procedures for application development quickly form a product solution.
```
SDK directory structure:
|--sdk
 |--csi_core 	//CSI-Core related interface definition, and interface implementation on
                //E902.
 |--csi_dirver  //CSI-Driver related interface definition, and peripheral Driver
                //implementation.
 |--csi_kernel  //CSI-Kernel related interface definition, and Rhino, FreeRTOSv8.2.3
                //ucos-iii and other real-time operating system docking example code
 |--libs        //Store common library implementations
 |--projicet	//Store a variety of reference examples including benchmark test
                //program, driver example program, rtos example program. The relevant
                //project documents are also included.
 |--utilites	//Store project config files.
 |--VERSION
```
    1. Download and install the CDK
    2. Open a project using CDK, for example open the hello project:
      projects/examples/hello_world/CDK/wj100-open-hello_world.cdkproj
    3. Build the project:
    Click "project" on the toolbar,and select "build all". After successful compilation, you will see the following:

```
Build target ' wujian100_open-hello_world BuildSet '
----------Building project:[ wujian100_open-hello_world - BuildSet ]----------
make[1]: Entering directory 'D:/release/Wujian100_open-V1.0.0/Wujian100_open-V1.0.0/projects/examples/hello_world/CDK'
make[1]: Leaving directory 'D:/release/Wujian100_open-V1.0.0/Wujian100_open-V1.0.0/projects/examples/hello_world/CDK'
make[1]: Entering directory 'D:/release/Wujian100_open-V1.0.0/Wujian100_open-V1.0.0/projects/examples/hello_world/CDK'
linking...
size of target:
   text	   data	    bss	    dec	    hex	filename
  22680	   1628	   6660	  30968	   78f8	D:/release/Wujian100_open-V1.0.0/Wujian100_open-V1.0.0/projects/examples/hello_world/CDK/Obj/wujian100_open-hello_world.elf
checksum value of target:  0xE2B2C769 (491,388)
make[1]: Leaving directory 'D:/release/Wujian100_open-V1.0.0/Wujian100_open-V1.0.0/projects/examples/hello_world/CDK'
Executing Post Build commands ...
Done
====0 errors, 0 warnings, total time : 20s263ms====
```
    4. Run the project:
    Click "Debug" on the toolbar,and select "Start/Stop Dubegger".
# Reference  and Thanks
    The program model of GPIO refer to the DesignWare of Synopsys 
    The program model of Timer refer to the DesignWare of Synopsys 
    The program model of WDT refer to the DesignWare of Synopsys 
