+++ 
date = "2014-12-17"
title = "Installing and configuring Open-source chef-server on Ubuntu and Managing AWS ec2 instances using knife"
slug = "Installing and configuring Open-source chef-server on Ubuntu and Managing AWS ec2 instances using knife" 
tags = []
categories = ["technical"]
series = ["Theme", "Hugo","Chef","Ubuntu","AWS","EC2","knife"]
+++

Hello,

This is my first post on automation and configuration management and that too on Chef.

I personally invested a lot time to get going with Chef, because it is bit confusing for newbies to catch the pace, after searching and reading a lot I choose a Open Source Chef Server to use and I started with the installation.

The difference between Hosted Chef Server and Open-source Chef Server can be read [here.](https://blog.chef.io/there-is-one-chef-server-and-it-is-open-source/) 

It is a quite a troublesome installation of the Open-source chef server especially if you are doing first time and there are many things which are not well documented. Few considerations before the installation of chef-server is that your server should have minimum of 4GB of Memory.

I am using Ubuntu 12.04 LTS 64 bit in this tutorial.

There are various ways available to install chef server but I succeeded successfully to install by the following installation method, so here we go step by step installation of Open-Source Chef.

Get the copy of chef-server from the following links

For Ubuntu get it from

https://downloads.chef.io/chef-server/ubuntu/#/

For Redhat and Centos get it from

https://downloads.chef.io/chef-server/redhat/#/

select the right architecture of your system and download the setup to your local storage,you can know the architecture of your Linux system by the command ```lscpu | grep Arch```

After downloading the setup move it to the server where you are willing to install and configure the Chef Server.

**Before starting there are some important considerations to note**

* If you have PostgreSQL already installed and running on default port 5432, I would recommend you to change the port of PostgreSQL other than 5432 and restart the PostgreSQL server. This hack worked for me for successful installation.

* Set your host-name to resolvable DNS, you can see your hostname by the ```hostname -f``` and you can change it by editing the file ```/etc/hosts```

* In your security groups or Firewall add an inbound rule for port number 9462. because the chef-server 11 does not run webui on 4000 and 4040, though I added an Inbound rule for them, add 5432 and 22 for ssh access.

After doing all three preliminary steps then go to the directory where you configured your chef-server setup .deb file and run the following command to install the open-source chef-server, in my case it was,

`sudo dpkg -i chef-server_11.1.6-1_amd64.deb`

Fingers crossed it will take few minutes to install and configure the chef-server

If your chef-server is installed successfully, you can run next command,

`sudo chef-server-ctl reconfigure`

it will reconfigure your chef-server passing your systems parameter and starting the required services such as rabbitmq and postgres.

After successful execution of above command run the following command to test the configuration.

`sudo chef-server-ctl test`

and if it returns success, yes you installed the chef server successfully Congratulations :p

restart the chef server once by the following command

`sudo chef-server restart`


Now to access the chef-server WebUI a small hack has to be done, I did on my server is to

edit the file edit `/etc/chef-server/chef-server-running.json`

find line

`cookie_domain=”false”`,

and replace it by

`cookie_domain=”FQDN”`,

Now once again reconfigure and restart chef-server by running following commands

`sudo chef-server-ctl reconfigure`

`sudo chef-server restart`


Now go to browser and enter the IP or domain of your server you may get SSL Certificate error because it is not yet configured, so add the exception and proceed further.

you will be redirected to the Chef-server webui Login Page

enter the default username as admin

and password is p@ssw0rd1

now login and first change the admin password

now there you can see your chef-server dashboard and all other tabs you can browse nodes,clients,roles etc.

So we are not yet done we didn’t do any useful work using chef-server!

So lets create an ec2 Instance but before that we need to install some gems

`gem install chef`

`gem install knife-ec2`

`gem install net-ssh-multi`


after installing these gems

create a directory named .chef in home folder or you can simply run the following commands:-

`mkdir -p ~/.chef`

`sudo chown -R $USER ~/.chef`

After it regenerate the private key from the Chef WebUi of Admin and copy to the

`/etc/chef-server/admin.pem`

also regenerate the private key of chef-validator client and copy it to

`/etc/chef-server/chef-validator.pem`

Run the following command

`knife configure -i`

For configuring knife, we need to pass few details:

Path for knife.rb file: default is `~/.chef/knife.rb`

Chef Server URL: `https://< Elastic-IP > orhttps://< EC2-Public-DNS >`

Name of the new user: `< any-desired-name >`

Name of the existing admin: `admin`

Location of admin’s private key: `/etc/chef-server/admin.pem`

Validation Key Name: `chef-validator`

Validation Key Path: `/etc/chef-server/chef-validator.pem`

Path of chef repository: `< default >`

New User Password: `< any-desired-password >`

after doing the knife configuration

add the following lines to knife.rb

`knife[:editor] = ‘/usr/bin/vim’`

`knife[:aws_access_key_id] = “”`

`knife[:aws_secret_access_key] = “”`

Note for the keys aws_key_id is the key ID of your AWS IAM user

and aws_secret_access_key is the secret key is also of the same user

Note the IAM user has to admin so that it can have access to create and delete Instances

So now all set and we are good to create an ec2 instance using chef-server

So use the following command to create your ec2 instance

`knife ec2 server create -r “role[blog-test]” -I ami-a74f62f5 -f m3.medium -S knife-ec2-test -i ~/.ssh/knife-ec2-test.pem –ssh-user ubuntu –region ap-southeast-1 -Z ap-southeast-1b`

"role[blog-test]" is the run_list I want to associate with the newly created node. You can put any roles and recipes you like here

* `-I` is the AMI ID selected for AMI image

* `-f` is the Amazon EC2 instance type (Also known as a Flavor)

* `-S` is the name you gave to the EC2 key pair generated in the AWS console

* `-i` points to the private key file of that EC2 key pair as downloaded when the keypair was created in the AWS console

* `--ssh-user` the official Ubuntu EC2 AMIs use ubuntu as the default user

* `--region ap-southeast-1` If you want your instances to be deployed in any specific Amazon AWS region, add this parameter and the desired region

* `-Z ap-southeast-1b` is the availability zone within your region (i.e. you have an existing disk volume you need to made available to this instance)

after running the command it will create an ec2 instance and install the chef client

also it will execute the recipes under the role test

Managing EC2 Instances with knife

to list all the servers in the cloud

`knife ec2 server list –region ap-southeast-1`

To delete the instances and nodes you can do it by following way:-

`knife kec2 server delete -i-xxxxxxx –region ap-southeast-1`

`knife node delete i-xxxxxxx`

So we have installed and configure the chef server and by using knife we have created an ec2 instance.
