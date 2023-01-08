# RokuTV-HTPC-AutoPower

The cheap TCL/RokuTVs seem to powerdown automatically at idle which makes things quite annoying if attached to a PC or HTPC. 

Majority of GPUs do not support CEC and units like the Pulse Eight HDMI-CEC USB adapter are $50 just to turn a TV on and Off

Luckily the RokuAPI (External Control Protocol (ECP) allows us to do this for free

This is setup on windows but extremely easy to setup on Linux/MacOS as well.

## Setup

bat scripts:
Grab IP address of RokuTV (static IP recommended)


Modify poweron-tv.bat with IP address. Example:

 ```curl -d '' "http://<IPADDRESS>:8060/keypress/powerOn"```

Modify poweroff-tv.bat with IP address. Example:

```curl -d '' "http://<IPADDRESS>:8060/keypress/powerOff"```

## Usage

Press Windows + R, and type “taskschd.msc“ to open Task Scheduler. Select "Create Task"

![image](https://user-images.githubusercontent.com/31908995/211224114-2bcf841c-c384-4825-b7ce-016f6d6877cb.png)


Name the task whatever you want. I named it poweron-tv & poweroff-tv. make sure to select "Run whether user is logged on or not"

![image](https://user-images.githubusercontent.com/31908995/211224157-7acc7980-8fe5-4989-a822-4f55efaa4c96.png)

Go to "Triggers" tab and select "New" 

Add the following for poweron-tv:

![image](https://user-images.githubusercontent.com/31908995/211224159-8e4d99dc-bd57-42e7-80b1-c76712802eaf.png)

Add the following for poweroff-tv:

![image](https://user-images.githubusercontent.com/31908995/211224161-62573059-89da-4216-917d-412c8335cc92.png)

Go to "Actions" tab > New. Action = Start a program. Program/Script is the on/off .bat file.

![image](https://user-images.githubusercontent.com/31908995/211224171-2680b472-3f17-42dd-b341-93b7ed4c26d4.png)

That's it. TV will now PowerOff at lock screen/idle and Power On at startup/unlock
