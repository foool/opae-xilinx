# First, install Docker on Ubuntu.

>
>```bash
>    sudo apt update && sudo apt upgrade
>    sudo snap install docker --stable
>    sudo groupadd docker
>    sudo usermod -aG docker $USER


# Then, create a new docker VM.

>
>```bash
>    source create_container.sh

## Inside the docker VM, download the OPAE source code(Drivers), and then build and install them.

>
>```bash
>    cd shared
>    source install_opae_drv.sh

## At this point, the FPGA device node can be seen in the host's sysfs, but not in the docker VM's sysfs.

>
>```bash
>    # Run the following in the host and in the docker VM, to check the driver status
>    ls /dev/intel-fpga-port.0 
>    ls /sys/class/fpga/intel-fpga-dev.0/intel-fpga-port.0/

## Exit from the docker VM.

>
>```bash
>    exit

## ReStart the docker VM, without recreating it.

>
>```bash
>    source start_container.sh

## At this point, the FPGA device node can be seen in both the host and the docker VM.

>
>```bash
>    # Run the following in the host and in the docker VM, to check the driver status
>    ls /dev/intel-fpga-port.0 
>    ls /sys/class/fpga/intel-fpga-dev.0/intel-fpga-port.0/


## Inside the docker VM, download the OPAE source code(SDK), and then build and install them.

>
>```bash
>    cd shared
>    source install_opae_sdk.sh

## A successful run's printout

>
>```bash
>    Using OPAE C library version '1.3.0' build 'unknown'
>    Running Test
>    token_list.c:241:token_get_parent() **ERROR** : can't find parent in: /sys/class/fpga/intel-fpga-dev.0/
>    Running on bus 0x00.
>    AFU_CDMACR@0x10000 = 0x0000
>    AFU_CDMASR@0x10004 = 0x0002
>    I buffer physical address 0x0000000116400000
>    O buffer physical address 0x000000005c200000
>    AFU_CDMASR@0x10004 = 0x0000
>    AFU_CDMASR@0x10004 = 0x1002
>    Done Running Test


