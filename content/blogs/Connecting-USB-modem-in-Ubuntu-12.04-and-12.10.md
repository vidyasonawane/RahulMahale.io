+++
date = "2013-08-14"
title = "[Solved]Connecting USB modem in Ubuntu 12.04 and 12.10."
tags = ["Ubuntu","Linux","USB Modem"]
categories = ["Technical blogs"]
+++

Hi Ubuntu Users, 

you might just install the newly fresh Ubuntu 12.04 or Ubuntu 12.10, but you might not get the connection to the internet by using USB modem. You can’t directly connect internet connection by just plugging USB device and setting the internet connection. Ubuntu developers and Canonical Community didn’t notice the small bug of network connection manager, the problem is that modem does not get detected, so we can’t set up to the internet settings. So in this blog, I will be publishing a very simple technique to connect to the Internet connection by using a USB modem.

If you have just installed the Ubuntu the first step is to create the root account in Ubuntu because Ubuntu and Debian based operating Systems doesn’t have the root account. So we will have to create it by just entering the following command,

`Sudo passwd` Entering this command on the terminal will ask you for password and it will create a root account with the same password. Now you have to login as a superuser, so enter the following command `Su`

Enter your root password

Now, you have to plug your USB modem

After plugging, check if your modem is mounted or not by the following command

`lsusb` 

![lsusb](/images/lsusb.png)

This command will list all the drives and USB devices of your system.

Just check your USB is mounted or not. It is mounted but not detected, so for setting up internet connection enter the following command:

`modprobe –v option`

![modprob](/images/modprobe.png)

modprobe is a command to add and remove modules from Linux Kernel.

`–verbose`

Print messages about what the program is doing. Usually, modprobe only prints messages if something goes wrong. This option is passed through install or remove commands to other modprobe commands in the MODPROBE_OPTIONS environment variable.

After that, you just have to enter the following command

`echo”1c9e 9605″ > /sys/bus/usb-serial/drivers/option1/new_id`

This command will write the entry for the modem in the new_id file

That’s all now your modem is detected and you can set up your internet connection through a network manager.

