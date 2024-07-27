# Nvidia

* I got this one [youteetoo](https://www.youyeetoo.com/products/jetson-nano-b01-subkit-nano-kit?VariantsId=10564)
* I thought it was this one [youteetoo](https://www.youyeetoo.com/blog/detail/jetson-nano-module-b-with-16g-emmc-nv0031-nv0030-35)
* I *think* use of SD card vs EMMC is enabled via this device-tree mod[youteetoo_wiki](https://wiki.youyeetoo.com/en/JETSON_NANO/Firmwareupdate)

* [Nano_FAN_issues](https://gr33nonline.wordpress.com/2022/07/04/jetson-nano-fan-issues/)
* [Jetson_Hacks](https://jetsonhacks.com/2019/10/10/jetson-nano-uart/)

* [Arrow datasheets](https://static6.arrow.com/aropdfconversion/d6d7d39921458360765c21faf5c22a3988a06ba9/jetson-nano-devkit-datasheet.pdf)
* [SiliconHighway_datasheet](https://siliconhighway.com/wp-content/gallery/jetson-nano-module-datasheet-us-1031771-r3-hr.pdf)
* [Arrow_other](https://www.arrow.com/en/products/945-13450-0000-000/nvidia)
* [Nvidia_datasheet](https://developer.nvidia.com/embedded/dlc/jetson-nano-system-module-datasheet)
---
# Other folks
* [Jetson_Easy_setup](https://github.com/rbonghi/jetson_easy)
* [Jtop](https://github.com/rbonghi/jetson_stats)

* [Update_to_20.04](https://qengineering.eu/install-ubuntu-20.04-on-jetson-nano.html)

* [Installing_OpenCV](https://github.com/Qengineering/Install-OpenCV-Jetson-Nano)
* [QEngineering_Jetson_Nano](https://qengineering.eu/install-opencv-on-jetson-nano.html)

* [Dusty_Franklin_Jetson_Utils](https://github.com/dusty-nv/jetson-utils)

* [AAEON_Boxer_8221AI-B1_Jetson_Nano_images](https://partnerzone.aaeon.com.tw/NAS/directory/Projects/BOXER-8221AI-B/Images/)

* [Yocto_Open_Embedded_for_Tegra](https://github.com/OE4T)
* 
  
---
# DOCS

* [Jetson Wiki](https://elinux.org/Jetson)
* [Dev_Kit_Users_guide](https://developer.nvidia.com/embedded/downloads#?search=Jetson%20Nano%20Developer%20Kit%20User%20Guide)
* [Getting_Started](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit)
* [Nano_resources](https://devtalk.nvidia.com/default/topic/1048642/jetson-nano/links-to-jetson-nano-resources-amp-wiki/)
* [Other](https://developer.nvidia.com/embedded/downloads#?search=module%20data%20sheet)

---
* [Forum](https://devtalk.nvidia.com/default/board/139/embedded-systems/1)
* [Boot_from_USB](https://jetsonhacks.com/2021/03/10/jetson-nano-boot-from-usb/)
* [Boot_from_USB_github](https://github.com/JetsonHacksNano/bootFromUSB)
  

# Ubuntu USER:nvidia PWD:nvidia

---
[youyeetoo shop](https://youyeetoo.com/nvidia-jetson-tx2-development-kit-8-gb-128-bit-lpddr4-32-gb-emmc-the-ai-solution-for-autonomous-machines-p0017.html)
[Aliexpress](https://www.aliexpress.com/item/32918486835.html)

---
# FAN issue

https://www.youyeetoo.com/products/jetson-nano-b01-subkit-nano-kit?VariantsId=10564


“sudo jetson_clocks --show”  

sudo sh -c ‘echo 255 > /sys/devices/pwm-fan/target_pwm’ 

ON :
sudo sh -c ‘echo 255 > /sys/devices/pwm-fan/target_pwm’

OFF :
sudo sh -c ‘echo 0 > /sys/devices/pwm-fan/target_pwm’
(slowly turned off)


https://github.com/Pyrestone/jetson-fan-ctl


Before launching jetson_clocks.sh script for boosting, 
you can store your clocks config into file /home/ubuntu/l4t_dfs.conf and later restore with :

```
sudo /home/ubuntu/jetson_clocks.sh --store       # save clocks config into l4t_dfs.conf file
sudo /home/ubuntu/jetson_clocks.sh               # boost clocks
sudo /home/ubuntu/jetson_clocks.sh --restore     # restore clocks config from l4t_dfs.conf file
```

Back to slow clocks, after a while when heat will have decreased enough, the fan will stop.

---
# EDIMAX WiFi

* [These instructions are from SPARKFUN](https://learn.sparkfun.com/tutorials/adding-wifi-to-the-nvidia-jetson/all)

--
## Download the N150 Drivers

You can download the appropriate drivers by opening a terminal and entering the following command:


* git clone https://github.com/lwfinger/rtl8723bu.git [Enter]

Once the download is complete you can navigate into the drivers directory with the following command:

* cd rtl8723bu and then [Enter]

You are now in the the directory (folder) to start the install process for the drivers!
## Installing the Drivers

There are a couple of methods to install these drivers on a single board computer or really any other Linux computer. You can check out the README file of the GitHub repository to compile and install them from scratch, but we are going to install them through Dynamic Kernel Module Support (DKMS). These instructions can be found at the bottom of the README for the drivers, but we will reiterate them here.

Assuming you are still in the driver directory named “rtl8723bu” type the following command:

* source dkms.conf [Enter]

Once you get the command prompt back (which should almost be instantaneous) type the following command to create a working project directory:

* sudo mkdir /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION [Enter]

With the directory created, type the following to move a number of files to your working project directory:

* sudo cp -r core hal include os_dep platform dkms.conf Makefile rtl8723b_fw.bin /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION [Enter]

We finally add those files to DKMS with by executing the following command:

* sudo dkms add $PACKAGE_NAME/$PACKAGE_VERSION [Enter]

Now that everything is ready and in its place we can finally install the drivers by typing the following command:

* sudo dkms autoinstall $PACKAGE_NAME/$PACKAGE_VERSION [Enter]

DKMS will take a number of actions to install the drivers including cleaning up after itself and deleting unnecessary files and directories. Once the DKMS completes the installation you should get a positive confirmation of the installation!

With the installation complete it is a good idea to reboot your Nvidia Jetson Nano with this command:

* sudo reboot now [Enter]
---

