# ESP32 MJPEG Streaming Server

This is a simple MJPEG streaming webserver with static IP implemented for the project of small semester. 
It can create a MJPEG streaming webserver with unchanged URL given the gateway (the subnet should cover the preset IP. See `How to use`)
Forked and modified from <https://github.com/arkhipenko/esp32-cam-mjpeg>. Tested on AI thinker ESP-32 CAM.

## Why static IP
The main reason is that I cannot read the serial and see the IP address after each connection. My mobile hotspot doesn't support disabling DHCP, so what I can only do is to let my ESP32 CAM finish it. 

## Before Using
1. Open the project file with arduino IDE.
2. Create a file called `home_wifi_multi.h` at the project folder.
3. Define the SSID and PWD of your Wifi by placing the following into it.
```C
#define SSID "replace with your wifi ssid"
#define PWD "replace your wifi password"
```
4. Save the file.
5. Compile and upload the project.

## How to use
### If you can read the serial
Power it on and read the serial. It will show you the address of the stream.
### If you cannot read the serial
1. Connect your device (laptop for example) to the Wifi you specify in the step `Before Using`.
2. See the gateway of your laptop (for windows you can refer here: <https://www.noip.com/support/knowledgebase/finding-your-default-gateway>).
3. Change the last number of the gateway into `15` (If you want to change this number, please refer to the code. Changing it into other numbers is not needed in the project so the only way to change the number is to change the `15` in the second connection in the code into other numbers).
4. Aha! Now you get the IP address of the ESP32 CAM. Visit `http://<your ESP32 CAM IP>/mjpeg/1` for video streaming and `http://<your ESP32 CAM IP>/jpg` for image capturing.

## Warning
The cam is single thread so never try to use multiple devices to visit the streaming. 
