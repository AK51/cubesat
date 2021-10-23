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

Start your Pi4

Type in the following in the terminal

bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)

node-red-pi --max-old-space-size=256

sudo systemctl enable nodered.service

sudo reboot

I assume you know about node-red (If not, pls google/youtube the info.)

Import the text from code.txt

Install the proper library yourself


Here is the BOM list

1	3D structure (https://www.thingiverse.com/thing:4096437)

2	Raspberry Pi battery board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dXlh2PI&id=601128467001&_u=410e9q3560ce)

3	18650 battery x 2

4	Raspberry Pi with heatsink and power supply

5	GPS module (ATGM332D)

6	CSI Camera

7	40 pin extender

8	Raspberry Pi A/D Extension board (https://item.taobao.com/item.htm?spm=a1z09.2.0.0.13702e8dR0UVmn&id=646405407663&_u=410e9q359331)

9	MPU9250 (Accelerometer, Gyro and Magnetic field sensors)

10	Photosensors(TEMT6000) x 4 

11	Connection wires (female to female) 10cm

12	Sticky tape and bluetag (https://detail.tmall.com/item.htm?id=598167581834&spm=a1z09.2.0.0.13702e8diUmNw0&_u=410e9q35bf91)

13	M2.5/M3 screws and stand off


For the image file (or even the whole kits set), if you need it, please PM me at u3541219@connect.hku.hk.

Thanks
