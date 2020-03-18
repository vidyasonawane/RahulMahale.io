+++
date = "2014-09-03"
title = "[Solved] Running Cron job at reboot on Raspberry Pi in Debian(Wheezy) and Raspbian."
tags = ["Raspbian","Cron job"]
categories = ["technical blogs"]
+++

Hello Pi users,

After investing much time than expected to run a cron job at reboot in Rapbian. finally, I am able to run the cron job at startup and able to execute the necessary commands at start-up.

It is quite Obvious that `@reboot` will run the cron job at startup but in Raspbian and Debian (wheezy) it is not the case.

`@reboot` does not work as expected and it is a bug in debian you can read it [here](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=635473)

So here are the steps to for running cron job at reboot:-

* log in to your pi using ssh

* switch to root user using `sudo bash`

* run the command `crontab -e`

* put your command as `@reboot bash /path/to/file/run.sh` save it and get back on the terminal

* then start cron service by running `/etc/init.d/cron start`

* then one additional step is to edit the `/etc/rc.local` file and add the following line in `/etc/init.d/cron/start`  be sure that it should before exit 0.

* now reboot your system by command `reboot`

and now your cron job is started you can check it by command `ps aux | grep cron`

also you can check the log tail `/var/log/syslog`.