# cubesat
How to make a cubesat

![77](https://user-images.githubusercontent.com/8468724/138394448-fa24b3db-534f-460e-a696-4718366a1069.jpg)

![github](https://user-images.githubusercontent.com/8468724/138434055-b095bcbc-7dda-4cec-becb-fe52057c542e.jpg)

![github1](https://user-images.githubusercontent.com/8468724/138435066-fdff597f-a795-44e3-85ae-457064cec861.jpg)

Introduction of the cubesat
https://youtu.be/Dau8FqqLi7g

Tutorial of the building procedure.
https://youtu.be/wTbtjWj2FSM


It is not easy to find a place to store a 32Gb image, here is the alternative

//Start your Pi4

In the Preference>Raspberry Pi Configuration>Interface, Enable the camera, I2C, Serial Port, Disable serial console

//Install Camera and Node-red (Reference: https://elinux.org/RPi-Cam-Web-Interface)

Type in the following in the terminal

```
sudo su (enter password)

apt-get update - y

apt-get upgrade -y

git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git

cd RPi_Cam_Web_Interface

./install.sh

bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)

sudo systemctl enable nodered.service

sudo npm install -g n

sudo n 10.24.0

sudo reboot
```
Go to http://localhost/html/

Select Camera Setting, then go to rotation and select 270

//Install library

Goto Web Browser and type in the address of 127.0.0.1:1880

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

open another tab in the web browser and type in 127.0.0.1:1880/ui for the cubesat UI.
The color and theme can be changed. You should see the white background.



Here is the BOM list

1	3D structure (https://www.thingiverse.com/thing:4096437)

2	Raspberry Pi battery board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dXlh2PI&id=601128467001&_u=410e9q3560ce)

3	18650 battery x 2

4	Raspberry Pi with heatsink and power supply

5	GPS module (ATGM332D)

6	CSI Camera

7	40 pin extender

8	Raspberry Pi A/D Extension board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dR0UVmn&id=646405407663&_u=410e9q359331)

9	MPU9250 (Accelerometer, Gyro and Magnetic field sensors) (Note: if you bought the 9255 instead, the magnetic field sensor won't work)

10	Photosensors(TEMT6000) x 4 

11	Connection wires (female to female) 10cm

12	Sticky tape and bluetag (https://detail.tmall.com/item.htm?id=598167581834&spm=a1z09.2.0.0.13702e8diUmNw0&_u=410e9q35bf91)

13	M2.5/M3 screws and stand off


For the image file (or even the whole kits set), if you need it, please PM me at u3541219@connect.hku.hk.

Thanks
