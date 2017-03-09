# click-on-camkes
###To start with:install repo and type the following
```
mkdir camkes-project
cd camkes-project
repo init -u https://github.com/AlanYiNew/click-on-camkes.git
repo sync
```

###After downloading all the files and folder
cd into camkes-project/libs and git clone https://github.com/AlanYiNew/libcpp.git libc++
cd into camkes-project/apps and git clone https://github.com/AlanYiNew/helloworld-camkes.git
vim ../Kconfig and add the following after libsel4muslccamkes in libraries menu
```
source "libs/libc++/Kconfig"
```
add the following in menu examples
```
source "apps/helloworld/Kconfig"
```
save it and type make menuconfig under the project folder. Configure toolchain prefix to arm-linux-gnueabi- under unbuntu environment and change the application to use helloword.

####last second step
Copy the https://github.com/AlanYiNew/sel4-common-tool/blob/master/common.mk into camkes-project/tools/common/
which should override the existing one

####Finally
make clean
make
qemu-system-arm -M kzm -nographic -kernel images/capdl-loader-experimental-image-arm-imx31
