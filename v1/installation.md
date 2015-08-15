# Installation
Itylos is really to install since you just have to copy the provided image to your SD card and insert it into your Raspberry Pi. Afterwards you just need to configure your Itylos instance. Itylos can also be installed on any platform provided it has java and a working mongo db instance.


## Installation using Itylos.io image

### 1.Download image
Download the corresponding image sutibale for your raspberry version and copy it to your SD card. Itylos image is built on Raspbian and has all the dependencied needed for Itylos to run (web UI, server, mongo db).
#### Download the image for Raspberry Model 2 (Recommended)
#### Download the image for Raspberry Model A, A+, B and B+

### 2.Burn image to sd card (linux)
To burn Itylos image to your SD card using ubuntu, we recommend you to use gparted. 
-  Open gparted and delete all partitions for your sd card. Afterwards create a new partition using fat 32 file system. Finally do not forget to apply all operations otherwise no changes will be made.
-  Unzip image using **7z e itylos-io-armvX.7z**
-  Transfer image using **sudo dd if="itylos-io-armvX.img" of=/dev/sdb bs=4M** *(This will take some minutes)*. 

### 3. Power on the Raspberry Pi
When the installation has finished, plug the SD card to your Raspberry Pi. Wait some minutes for the Raspberry to boot and at this point you need to find the IP address of the Raspberry PI or you can try to open **http://itylos.local** from your broswer. After you have succesffully connected to your Itylos instance you just need to login. The default credentials are admin@myhome.com/1234

![Login page kerberos.io webinterface](1_how-to-access.png)
