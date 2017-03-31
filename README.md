## How to use MySignals HW with Android phone using Unity 3d

What is needed:

* [MySignals HW](https://www.cooking-hacks.com/mysignals-hw-ehealth-medical-biometric-arduino-complete-kit-ble)
* Arduino Uno (not uncluded in the mySignals kit)
* Android phone
* [Arduino IDE](https://www.arduino.cc/en/Main/Software)
* [Unity 3d]()
* Android studio

### Basic concept

on Android you running two applications **Sender** and **Receiver**. **Sender** is receiving data coming from **MySignals BLE module** over Bluetooth and sending it to the **Receiver** which is a Unity App with a custom android plugin. **Sender** always running in the backround as **andorid service**

### Arduino setup
1. Install [Arduino IDE](https://www.arduino.cc/en/Main/Software)
2. Download [arduino library](http://www.cooking-hacks.com/media/cooking/images/documentation/mysignals_hardware/MySignals_HW_SDK_V2.0.0.zip). If this link broken you can download latest version here [MySignals Hardware SDK](https://www.cooking-hacks.com/mysignals-hw-ehealth-medical-biometric-iot-platform-arduino-tutorial/#step5)
3. Add all .zip libraries one by one to Arduino: **Sketch > Include Library > Add .ZIP Library**
5. Connect your board to computer. If there is no green light on the board just check the connection between mySignals board and Arduino Uno is strong.
6. Select board: **Tools > Board > Arduino/Genuino Uno**
7. Select port: **Tools > Port >** usually it should be something **/dev/cu.usbmodem1411/**
8. Upload some examples to the board to make sure everything is working. Open **File > Examples > MySignals > Sensor > sensor_airflow** then upload: **Sketch > Upload** and wait untill the message "upload done" appear. Now you can open **Tools > Serial monitor** to check data coming from the sensor. If you see weird characters just try to change **baud** at the bottom right.

### Android Studio
1. Create new project App Name : MySignalsReceiver, Company domain : yourname.com > next > Target Android devices: default settings > Empty Activity : MainActivity
2. f
