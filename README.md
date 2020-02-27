# ultra96v2
ultra96v2
PetaLinux Error : Build Error Anuino? Some Packaeg ?


Custom Image Generation by PetaLinux 2019.2
--------------------------------------------
location : $TRD_HOME/pl/prj/, There is no more bit-generation & xsa(hardware platform)

  >> petalinux-create --type project --template zynqMP --name test1
  
  
<< log >>  
redrabbit@redrabbit-crossworks:~/work/Resnet50_Ultra96v1_2019_2/pl/prj$ ll
total 12
drwxrwxr-x 3 redrabbit redrabbit 4096  2월 27 11:42 ./
drwxrwxr-x 8 redrabbit redrabbit 4096  2월 27 11:42 ../
drwxr-xr-x 8 root      root      4096  2월 27 12:14 ultra96/
redrabbit@redrabbit-crossworks:~/work/Resnet50_Ultra96v1_2019_2/pl/prj$ petalinux-create --type project --template zynqMP --name test1
INFO: Create project: test1
INFO: New project successfully created in /home/redrabbit/work/Resnet50_Ultra96v1_2019_2/pl/prj/test1
redrabbit@redrabbit-crossworks:~/work/Resnet50_Ultra96v1_2019_2/pl/prj$ ls
test1  ultra96
redrabbit@redrabbit-crossworks:~/work/Resnet50_Ultra96v1_2019_2/pl/prj$ 




  >> petalinux-config --get-hw-description=../ultra96/   no file name. just folder    (top_wrapper.xsa)
  Real Input :
  >> petalinux-config --get-hw-description=/home/redrabbit/work/Resnet50_Ultra96v1_2019_2/pl/prj/ultra96/


1. DTG Settings ---> ultra96v2_resnet (make hw board/device template)
2. Image Packaging Configuration ---> Root filesystem type (INITPARAMS) ---> (x) EXT (SD/eMMC/QSPI/SATA/USB)
3. Yocto Settings ---> Enable Debug Tweaks

-----> Save @ $TRD_HOME/pl/prj/project-spec/configs/config ---> OK ---> Exit

redrabbit@redrabbit-crossworks:~/work/Resnet50_Ultra96v1_2019_2/pl/prj/test1$ petalinux-config --get-hw-description=/home/redrabbit/work/Resnet50_Ultra96v1_2019_2/pl/prj/ultra96/
INFO: Getting hardware description...
INFO: Rename top_wrapper.xsa to system.xsa
[INFO] generating Kconfig for project
[INFO] menuconfig project


*** End of the configuration.
*** Execute 'make' to start the build or try 'make help'.

[INFO] sourcing bitbake
[INFO] generating plnxtool conf
[INFO] generating meta-plnx-generated layer
[INFO] generating user layers
[INFO] generating workspace directory
[INFO] generating machine configuration
[INFO] generating bbappends for project . This may take time ! 
[INFO] generating u-boot configuration files
[INFO] generating kernel configuration files
[INFO] generating kconfig for Rootfs
[INFO] silentconfig rootfs
[INFO] generating petalinux-user-image.bb


/project-spec/meta-user/conf 

  >> vi user-rootfsconfig
  revised file.
  
  >> petalinux-config -c rootfs
  
  ---> Filesystem Package ---> misc ---> v4l-utils ---> check "v4l-utils", "libv4l", "media-ctl"
  ---> yavta ---> yavta
  ---> gdb ---> check "gdb", "gdbserver"
  
  cd
  
  ----------------------------------------------------------------------------------------------------------------
  






