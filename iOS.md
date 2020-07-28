# iOS

Some functions are diabled by default:

* `switchWifi()`
* `switchBluetooth()`
* `switchLocation()`
* `switchAirplane()`
* `isBluetoothEnabled()`
* `addBluetoothListener()`

When you call these functions, you'll just get some warning log.

You can enable it by add a preprocessor macros.

## Private API

There are some functions which start with `switch`:

* `switchWifi()`
* `switchBluetooth()`
* `switchLocation()`
* `switchAirplane()`

I implement them by using non-public APIs, which is not permitted on the App Store, see [this issure](https://github.com/c19354837/react-native-system-setting/issues/28). 

**These functions are disabled by default. You must not call them If your app need submit to App Store. As an alternative, you can show a tip to tell the user how to change the system setting.**

Only when you'll distribute the app outside App Store, you can enable them by add a preprocessor macros `PRIVATE_API`.

**WARNING: If you enable it and submit app to App Store, you'll definitely get a rejection from apple. In the worst case, your account will be ban!**

![add preprocessor macros `PRIVATE_API `](./screenshot/ios_private_api.png)

> You should add `PRIVATE_API` in both `Debug` and `Release` 

## Bluetooth

There are some bluetooth-function:

* `isBluetoothEnabled()`
* `addBluetoothListener()`

You can enable them in a few steps: 

First, add preprocessor macros `BLUETOOTH`

![add preprocessor macros `BLUETOOTH`](./screenshot/ios_bluetooth.png)

> You should add `BLUETOOTH` in both `Debug` and `Release`

Then open `Info.plist` as source code.

![open Info.plist as source code](./screenshot/ios_bluetooth_plist.png)
 
Finally, add `NSBluetoothPeripheralUsageDescription` in `Info.plist`, see [Info.plist - example](https://github.com/c19354837/react-native-system-setting/blob/master/examples/SystemSettingExample/ios/SystemSettingExample/Info.plist#L55-L56)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  
  ...
  
  <key>NSBluetoothPeripheralUsageDescription</key>
  <string>Explain the reasons for accessing...</string>
  
</dict>
</plist>
```

> You can change the `string` as you need

