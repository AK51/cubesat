# **cubesat**
**How to make a cubesat**

![77](https://user-images.githubusercontent.com/8468724/138394448-fa24b3db-534f-460e-a696-4718366a1069.jpg)

![github](https://user-images.githubusercontent.com/8468724/138434055-b095bcbc-7dda-4cec-becb-fe52057c542e.jpg)

![github1](https://user-images.githubusercontent.com/8468724/138435066-fdff597f-a795-44e3-85ae-457064cec861.jpg)

**Introduction of the cubesat**
https://youtu.be/Dau8FqqLi7g

**Tutorial of the building procedure.**
https://youtu.be/wTbtjWj2FSM

##########################################################################################################

For software there are 2 options

**Option 1: clone the 32Gb SD card**

Copy this 6Gb file

https://drive.google.com/drive/folders/137SgdFFk7QnPQ8T41HE4RwFZ36nAwzVp?usp=sharing

I have a linux computer (if you only have a window, please unzip the file and use the traditional way to burn the image to the SD card, I have not tried it myself though)
```
# check the SD card location, is it sdb or sdc or sdd...

sudo parted -l

sudo su

gunzip -c /home/<login name>/sta_20211025.img.gz | dd of=/dev/sdX bs=64K
  
#If my login is Andy and my SD card is located in sdb
  
#Then the command will be,

gunzip -c /home/Andy/sta_20211025.img.gz | dd of=/dev/sdb bs=64K
```

**Option 2: Build the system**

  **Start your Pi4**

  In the Preference>Raspberry Pi Configuration>Interface, Enable the camera, I2C, Serial Port, Disable serial console

  **Install Camera and Node-red**

  Type in the following in the terminal

```
sudo su (enter password)

apt-get update - y

apt-get upgrade -y

sudo apt-get install i2c-tools python-smbus

git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git

cd RPi_Cam_Web_Interface

./install.sh

cd ~

bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)

sudo systemctl enable nodered.service

sudo npm install -g n

sudo n 10.24.0

sudo reboot
```
  **Go to http://localhost/html/**

  Select Camera Setting, then go to rotation and select 270

  **Install library in Nodered**

  Goto Web Browser and type in the address of **127.0.0.1:1880**

  Follow this youtube to install dashboard (https://www.youtube.com/watch?v=7QOWxuuGYh4)

  node-red-dashboard

  Do the same thing for 

  node-red-contrib-i2c

  node-red-contrib-nmea

  node-red-contrib-web-worldmap

  node-red-contrib-python-function

  node-red-contrib-python3-function

  node-red-contrib-mpu9250

  Copy the text from the code.txt in this github

  Import the flow (follow this video for import, https://youtu.be/vLhVxWRtWc8?t=168)

  Note: you may need to delete the node, remove it in manage palette and reinstall the node in order to get the right version. (I did it in serialport, I2C and MPU9250)

The software setup is done.

**END of option2**

##########################################################################################################

open another tab in the web browser and type in **127.0.0.1:1880/ui** for the cubesat UI.

The color and theme can be changed. You should see the white background.



**Here is the BOM list**

1	3D structure (https://www.thingiverse.com/thing:4096437)

2	Raspberry Pi battery board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dXlh2PI&id=601128467001&_u=410e9q3560ce)

3	18650 battery x 2

4	Raspberry Pi with heatsink and power supply

5	GPS module (ATGM332D)

6	CSI Camera

7	40 pin extender

8	Raspberry Pi A/D Extension board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dR0UVmn&id=646405407663&_u=410e9q359331)

9	MPU9250 (Accelerometer, Gyro and Magnetic field sensors) (Many counterfeit items in the market, the compass does not work)

10	Photosensors(TEMT6000) x 4 

11	Connection wires (female to female) 10cm

12	Sticky tape and bluetag (https://detail.tmall.com/item.htm?id=598167581834&spm=a1z09.2.0.0.13702e8diUmNw0&_u=410e9q35bf91)

13	M2.5/M3 screws and stand off

Note: 
1. If the compass does not work, please download the MPU9250.py, then type in the following in the terminal
```
i2cdetect -y 1
```
If you don't see 0C address, the board is faulty

And run this code under the same folder of the MPU9250.py, if there is no error, the board should be ok.
```

python MPU9250.py
```
I bought 3 MPU9250 and 2 of them do not have 0C address, only one works.

Reference: https://makersportal.com/blog/2019/11/11/raspberry-pi-python-accelerometer-gyroscope-magnetometer (do not change the /boot/config.txt as the max speed is only 400Hz)


2. the image file is 6Gb, my google drive may not be avaiable after 2022 summer.
For the image file (or even the whole kits set), if you need it, please PM me.

**Advance setting**

Connect the Raspberry Pi to a router

Use ifconfig to check its IP address

Use a laptop to access the UI by typing the ip address:1880/ui (replace the 127.0.0.1)  
  
The laptop is acted as a ground station.

  
Cheers,
Andy
