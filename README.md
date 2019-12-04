# openstorage
Overview
____________________

This Raspberry pi project is innovated to ease data transfer b/w hard-disk to many no of devices at a time.
Lets get overview of this project through an example.
Assume we are on a class of 60 students and teachers are  willing to gave us notes which is about 20 to 30 GB in size. Then how they will provide us notes.

First case:-
---------------------------------------------------------------------------------------------------------------
They might gave their pen-drive to each and every student and wait till all students finished coping it.
But this whole process consume lots of time.
Second case:-
---------------------------------------------------------------------------------------------------------------

Sir may upload this whole 30 GB file to Google drive
But wait Google provide only 15 GB of free space per account.
So this idea fails to.
To solve this problem I innovated a method using device raspberry pi.
How this Device work:-
---------------------------------------------------------------------------------------------------------------

Raspberry pi generate wi-fi hotspot which created a web link(Own cloud) running over apache2 server.
So whenever someone connected Pen-drive/hard-disk to raspberry pi device it automatically detect it and ready to send/download file over that web link.
To download file which are in the pen-drive/hard-disk user need to do following steps:-
1. User should be connect to wi-fi hotspot(password=123456789) which are generated by raspberry pi.
2.  after this user need to go into browser and type this url http://10.10.0.1/owncloud/ after this a webpage is open user need to login through it.
(Note: Replace 10.10.0.1 with your raspberry pi ip adress )
Login id: root
Password: 12345
Voila all pen-drive/hard-disk file will appears at ones
Now user is able to download all the required files.
We can use this in various numbers of ways :-
1.	While travelling then we can also use this device.
2.	We can use this in our friend group to transfer large amount of data.
Only limitation is our imagination.

How to install/config:-
-------------------------------------------------------------------------------------------------------------
Connect your raspberry pi through Ethernet cable onto laptop.
Type the following command:
-----Git clone http://
Sudo su

Cd easy_data_sharing_using_raspberry_pi
python config.py
While running programme we have need to change some setting.
The following changes needs to be made in the Raspberry Pi configuration

a. Expand the root filesystem to have enough space for the cloud

Select Expand Filesystem

b. Change user password

For Security when accessing form the WAN

c. Change locale to en_US.UTF8

Select Internationalisation Options

d. Memory split, allocate 16M to video graphics

Select Advanced Options > Memory Split
and at last:-

You'll be prompted to enter the Pi User password. Then execute the underneath commands in blue:

MariaDB [(none)]> create database owncloud;

 Query OK, 1 row affected (0.00 sec)


MariaDB [(none)]> create user owncloud@localhost identified by '12345';

 Query OK, 0 rows affected (0.00 sec)


MariaDB [(none)]> grant all privileges on owncloud.* to owncloud@localhost identified by '12345';

 Query OK, 0 rows affected (0.00 sec)


MariaDB [(none)]> flush privileges;

 Query OK, 0 rows affected (0.00 sec)


MariaDB [(none)]> exit;

 Bye

After finish installing programme
This time to test it:-
----------------------------------------------------------------------------------------------------------------------------
1.make sure you reboot your Raspberry pi
2.Execute these following commands:-
sudo ifconfig wlan0 10.10.0.1
sudo /etc/init.d/isc-dhcp-server restart
Done..
Here you see an access point(pi_station) has been created. Connect it through using (password:123456789).

Now we need to config in .bashrc file to automatically run this programme on statup.
------------------------------------------------------------------------------------------------------------------------------
Cd
Nano .bashrc
Paste these following line:-
cd easy_data_sharing_using_raspberry_pi
Python auto.py
Save and exit.
Config raspberry to avoid login during statup
Sudo raspi-config
In boot option select auto login.
Now reboot 




 


 
