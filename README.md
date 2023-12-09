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

**Option 1: clone the ScanDisk 32Gb SD card**

Copy this 6Gb file for raspberry pi4
https://connecthkuhk-my.sharepoint.com/:u:/g/personal/u3541219_connect_hku_hk/EeMA2rluL11NkTAfJfFBQqsBv39SKGg0gq_xMYJPXCts-g?e=B3Rze2
#https://drive.google.com/drive/folders/137SgdFFk7QnPQ8T41HE4RwFZ36nAwzVp?usp=sharing

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

If you use raspberry pi3 B+
Copy this Big file for raspberry pi3 B+

https://drive.google.com/file/d/12o_1joOYlbikUlhbxVCIpO8TPeDFQjw4/view?usp=sharing
```
sudo parted -l
sudo su
gunzip -c cube3B.img.gz | dd of=/dev/sda bs=64K
```

Note: Don't use the SD card from different brand especially from China, the size is couple bytes smaller than the ScanDisk in which the clone cause error.

Note: I have heard you can also clone the SD card using this software too, https://www.raspberrypi.com/software/

**Option 2: Build the system**

  **Start your Pi4 or Pi3B+**

  In the Preference>Raspberry Pi Configuration>Interface, Enable the camera, I2C, Serial Port, Disable serial console

  **Install Camera and Node-red**

  Type in the following in the terminal

```
sudo su (enter password)

apt-get update -y

apt-get upgrade -y

sudo apt-get install i2c-tools python-smbus
Note: if python-smbus cannot be installed, it is still ok. It is embedded in some existing package already

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

  (Note: node-red-dashboard version is not compatible with my node-red version
  go to terminal
  cd ~
  cd ./node-red
  npm install node-red-dashboard@2.30.0
  )

  Do the same thing for 

  node-red-contrib-i2c

  node-red-contrib-nmea

  node-red-contrib-web-worldmap

  node-red-contrib-python-function

  node-red-contrib-python3-function

  node-red-contrib-mpu9250
  
  Reboot

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

5	GPS module (ATGM332D) (https://detail.tmall.com/item.htm?id=624586693428&spm=a1z09.2.0.0.6a222e8dwszrii&_u=k10e9q357f01)

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

3. For the Rpi3B+, it does not generate lots of heat so, we can skip the big heat sink and the 40pin header. Here are the pictures of the Rpi3B+ inside the CubeSat
![IMG_20220225_134206](https://user-images.githubusercontent.com/8468724/156783486-c87d45da-3e01-437e-81f7-528b9129d2bf.jpg)
![IMG_20220225_134224](https://user-images.githubusercontent.com/8468724/156783548-e734125c-3487-40c3-a4f2-f76ce66caa1a.jpg)
![IMG_20220225_134232](https://user-images.githubusercontent.com/8468724/156783734-1091b5f0-e737-4e7f-873d-e57f337688a9.jpg)
![IMG_20220225_134254](https://user-images.githubusercontent.com/8468724/156783790-e0dc4c86-effd-4d82-8b0c-89b7c503f2a2.jpg)

**Advance setting**

Connect the Raspberry Pi to a router

Use ifconfig to check its IP address

Use a laptop to access the UI by typing the ip address:1880/ui (replace the 127.0.0.1)  
  
The laptop is acted as a ground station.

  
Cheers,
Andy
