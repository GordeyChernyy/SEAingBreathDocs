## How to use MySignals HW with Android phone using Unity 3d

What is needed:

* [MySignals HW](https://www.cooking-hacks.com/mysignals-hw-ehealth-medical-biometric-arduino-complete-kit-ble)
* Arduino Uno (not uncluded in the mySignals kit)
* Android phone
* [Arduino IDE](https://www.arduino.cc/en/Main/Software)
* [Unity 3d]()
* Android studio

### Basic concept

You have to run two applications on Android:  **BridgeApp** and **UnityApp**. **BridgeApp** is receiving data coming from **MySignals BLE module** over Bluetooth and sending it to the **UnityApp** which is Unity app using a custom Android plugin. **Sender** is always running in the backround as **Android service**

### Arduino setup
1. Install [Arduino IDE](https://www.arduino.cc/en/Main/Software)
2. Download [arduino library](http://www.cooking-hacks.com/media/cooking/images/documentation/mysignals_hardware/MySignals_HW_SDK_V2.0.0.zip). If this link broken you can download latest version here [MySignals Hardware SDK](https://www.cooking-hacks.com/mysignals-hw-ehealth-medical-biometric-iot-platform-arduino-tutorial/#step5)
3. Add all .zip libraries one by one to Arduino: **Sketch > Include Library > Add .ZIP Library**
5. Connect your board to computer. If there is no green light on the board just check the connection between mySignals board and Arduino Uno is strong.
6. Select board: **Tools > Board > Arduino/Genuino Uno**
7. Select port: **Tools > Port >** usually it should be something **/dev/cu.usbmodem1411/**
8. Upload some examples to the board to make sure everything is working. Open **File > Examples > MySignals > Sensor > sensor_airflow** then upload: **Sketch > Upload** and wait untill the message "upload done" appear. Now you can open **Tools > Serial monitor** to check data coming from the sensor. If you see weird characters just try to change **baud** at the bottom right.

### Android Studio
1. Create new project **App Name : MySignalsReceiver, Company domain : yourname.com > next > Target Android devices: default settings > Empty Activity : MainActivity**
2. Go to **Res > Layout > Activity_main.xml**, double click it, drag button to component tree. Repeat for the second button.
3. Go to **Res > Values > Strings**, open in Editor, press plus button, **key: send button, Devault value: Start**, the same thing for the Stop button.Rename buttons IDs as ***start_button*** and **stop_button** respectively.
4. In Main_activity.java add 2 functions: 

``` Java
/** Called when the user taps the Start button */
    public void onStart(View view) {
        // Do something in response to button
    }

    /** Called when the user taps the Stop button */
    public void onStop(View view) {
        // Do something in response to button
    }
```

5. If you see View is highlighted with red, press Alt+Enter and Import class in drop-down menu.
6. Go to the button properties and rename the buttons.
7. Go to AndroidManifest.xml and paste this code after `</application>`

```xml
/** Called when the user taps the Start button */
    public void onStart(View view) {
        // Do something in response to button
    }

    /** Called when the user taps the Stop button */
    public void onStop(View view) {
        // Do something in response to button
    }

<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
    <uses-permission android:name="android.permission.BLUETOOTH_PRIVILEGED" />

    <uses-feature
        android:name="android.hardware.bluetooth_le"
        android:required="true" />
```

This allows bluetooth devices search. 

Paste this [code](link) into the MainActivity. Don't forget to replace package com.name to your name. 

Now we have to download and add [MySignals Android SDK](http://downloads.libelium.com/mysignals/mysignals_android/MySignalsConnectKit.jar.zip). Copy the unzipped file in Finder and go to to Project, open App and go to libs, select libs folder and press cmd+v. Then select mysignalsconnect.jar, right click > add as library. 

Now we'll create a new class BLEService for Bluetooth service. 


      
