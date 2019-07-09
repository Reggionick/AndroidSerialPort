# Description

[android-serialport-api](https://code.google.com/archive/p/android-serialport-api/)

[![](https://jitpack.io/v/kongqw/AndroidSerialPort.svg)](https://jitpack.io/#kongqw/AndroidSerialPort)

Step 1. Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

``` Gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

Step 2. Add the dependency

``` Gradle
dependencies {
        compile 'com.github.kongqw:AndroidSerialPort:1.0.1'
}
```

## View serial ports

``` Java
SerialPortFinder serialPortFinder = new SerialPortFinder();
ArrayList<Device> devices = serialPortFinder.getDevices();
```

## Open serial port

### Initialization

``` Java
mSerialPortManager = new SerialPortManager();
```

### Add open serial port listener

``` Java
mSerialPortManager.setOnOpenSerialPortListener(new OnOpenSerialPortListener() {
    @Override
    public void onSuccess(File device) {
        
    }

    @Override
    public void onFail(File device, Status status) {

    }
});
```

### Add data communication listener

``` Java
mSerialPortManager.setOnSerialPortDataListener(new OnSerialPortDataListener() {
    @Override
    public void onDataReceived(byte[] bytes) {
        
    }

    @Override
    public void onDataSent(byte[] bytes) {

    }
});
```

### Open serial port

- Parameter 1：Serial port
- Parameter 2：Baud rate
- return：Is the serial port open successfully?

``` Java
boolean openSerialPort = mSerialPortManager.openSerialPort(device.getFile(), 115200);
```

### send data

- Parameter：send data byte[]
- return：Whether the transmission was successful

``` Java
boolean sendBytes = mSerialPortManager.sendBytes(sendContentBytes);
```

## Close the serial port

``` Java
mSerialPortManager.closeSerialPort();
```

> PS：The transmission protocol needs to be packaged by itself.
