
# Triple Module Redundancy

## Licensing

The source and RTL files coming from thales-risc-v-registers-router, thales-risc-v-jtag-router, thales-risc-v-chisel-project and thales-risc-v-fault-detector are released under the BSD 3 clauses. 
The modifications of the Rocket-chip generator in the thales-risc-v-chisel-project are released under the BSD 3 clauses.
The rocket-chip generator is located at https://github.com/freechipsproject/rocket-chip.
The solution parts of the thales-risc-v-vivado and the bistream it generates are released under the BSD 3 clauses.
Modifications in the UltraScale+ linux, U-Boot, ZephyrOS and OpenOCD are released under GNU GPL v2 License.

## Thanks

We would like to thank Antmicro for the successful collaboration on this project.

## Running the demo straight away

This README file helps you regenerate the full project. For that you will need:
- chisel tools
- Vivado licence for the UltraScale+
- riscv-tools
- zephyr-sdk

## Source retrieval

Four IP cores have been written in chisel for this project.
- chisel-project
- registers-router
- jtag-router 
- fault-detector 

They are git submodules that need to be retrieved with the following script.

```Bash
./git.sh
```

## Bitstream generation

To regenerate the chisel projects, use this script

```Bash
./chisel.sh
```
It will generate verilog files that need to be copied in the thales-risc-v-vivado project.
To launch synthesis and implementation run the vivado.sh script. You will need to have vivado sourced here. 
It has been tested with vivado 2017.4.

```Bash
./vivado.sh
```
The resulting bitstream should be located in thales-risc-v-vivado/project_1/project_1.runs/impl_1/

## US+ Processing system software

If you want to regenerate the bootloader, the kernel and the RISC-V control software you can follow the instructions in **RISC-V-demonstrator--docs.pdf** - *5.1 US+ Processing system software* 

## RISC-V software

The RISC-V software consists of a ZephyrOS sample named im_alive. To re-generate it you will need to install the zephyr-sdk at https://docs.zephyrproject.org/latest/getting_started/installation_linux.html
After that, the `./make_im_alive.sh` script should correctly generate the RISC-V executable. It will be located at `riscv-zephyr/samples/im_alive/build/am_ft_devkit/zephyr/zephyr.elf`.

## SD card generation

To flash the SD card for the US+ target, you can use the instructions at **RISC-V-demonstrator--docs.pdf** - *6.1 Preparing the SD card*


