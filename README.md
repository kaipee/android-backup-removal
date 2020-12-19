# Android TV app backup and removal

## Prepare ADB connection

### Install ADB on your computer

Check the latest installation methods for your distro : https://www.google.com/search?client=firefox-b-d&q=easy+install+adb+linux

### Enable developer mode on Android TV

https://developers.google.com/cast/docs/android_tv_receiver/debugging#setting_up_for_development

1. Set up your Android TV device:
    1. Connect the Android TV device to the local network.
    1. Sign into your Google account.    
1. From the Settings, in the Device row, select About.
1. Scroll down to and click on Build several times until a dialog appears with the message, "You are now a developer."
1. Enable USB debugging:
    1. Install the USB cable, but don't connect the master end of the USB cable to your computer just yet.
    1. In the Preferences row, select Developer options, select USB debugging, and select On.
1. Navigate back to the home screen. You must do this to apply the settings you just selected. The settings will persist unless you perform a factory reset.

### Authorise your ADB client on the Android device

Connect to your Android device via its IP (i.e. 192.168.0.10 - you can find this under Network Settings).
```
adb connect 192.168.0.10:555
```

The Android device will prompt to authorise this ADB client. Enable and click **OK**.

## Usage
These commands will use Netflix as an example.

Assuming your device is an Android TV on the same network as your ADB client, using IP address `192.168.0.10` (example).

Set an environment variable.
```sh
export TV="192.168.0.10"
```

Find the package name using a filter.
```sh
./find $TV netflix
```

Backup a package and its data.
```sh
./backup $TV netflix
```

Restore a package and its data.
```sh
./restore $TV netflix
```

Remove a package.
```sh
./remove $TV netflix
```
