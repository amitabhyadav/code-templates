# C Project Template

On a Linux/Unix environment, to compile the project using GCC compiler execute the following:
```
make
```
or for detailed warnings and generating intermediate files, execute the following:
```
make DEBUG=1
```
or to remove the generated output files, execute:
```
make clean
```

you may also compile the program to a different architecture.
eg. if you have Xilinx Vitis 2021.2 installed and want to compile the project for Zynq-7000 ARM Cortex A9 32-bit architecture,
do the following:
```
source /opt/Xilinx/Vitis/2021.2/settings64.sh
export CROSS_COMPILE=arm-linux-gnueabihf-
make
```

### CONTRIBUTE
Please feel free to contribute to the template. Keep it simple and scalable. The idea is that the project structure can be adopted for large scale C projects with only minor to no modification.
