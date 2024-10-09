
<h1 align="center">
  <br>
  <a href="http://www.amitmerchant.com/electron-markdownify"><img src="https://raw.githubusercontent.com/brandonsaldan/nocturne-image/refs/heads/main/pictures/nocturne-logo.png" alt="Markdownify" width="200"></a>
  <br>
  nocturne-image
  <br>
</h1>

<h4 align="center">A pre-built Debian 13 image for the <a href="https://carthing.spotify.com/" target="_blank">Spotify Car Thing</a>.</h4>

<p align="center">
  <a href="#how-to-use">How To Use</a> •
  <a href="#download">Download</a> •
  <a href="#credits">Credits</a> •
  <a href="#related">Related</a> •
  <a href="#license">License</a>
</p>

![screenshot](https://raw.githubusercontent.com/brandonsaldan/nocturne-image/refs/heads/main/pictures/nocturne-1.png)

## How To Use

Unless receiving power through a Linux computer, running Nocturne on your Car Thing requires a host device such as a Raspberry Pi, a microSD card, a microUSB to USB-C cable, and a microUSB/your power source's connector. You will also need [superbird-tool](https://github.com/bishopdynamics/superbird-tool) to flash the image regardless of your computer's operating system.

### Windows

#### Raspberry Pi Setup

Download and open [Raspberry Pi Imager](https://downloads.raspberrypi.org/imager/imager_latest.dmg), select Raspberry Pi OS Lite (64-bit), select "Edit Settings", check "Set hostname", check "Set username and password" (set a password), check "Configure wireless LAN", (enter your network's SSID and password), check "Set local settings". Open the Services tab, enable SSH, and use password authentication. Write the configured OS to your microSD card and insert it into your Raspberry Pi.

#### Flashing Process

If you haven't already, download [superbird-tool](https://github.com/bishopdynamics/superbird-tool) and run the setup process detailed [here](https://github.com/bishopdynamics/superbird-tool?tab=readme-ov-file#supported-platforms).

Download and unzip [debian_v1.0_2024-10-08.tar.gz](TBD), connect Car Thing to your computer in USB Mode (hold preset buttons 1 and 4 while connecting), and run the following from your command line:

```bash
# Go into the superbird-tool repository
$ cd C:/path/to/superbird-tool-main

# Find device
$ python superbird_tool.py --find_device

# Flash Nocturne image
$ python superbird_tool.py --restore_device C:/path/to/debian_v1.0_2024-10-08

# Disable charger check
$ python superbird_tool.py --disable_charger_check
```

Connect your Raspberry Pi to your computer and run the following from your command line:

```bash
# Clone this repository
$ git clone https://github.com/brandonsaldan/nocturne-image

# Transfer setup_host.sh to Raspberry Pi
$ scp /path/to/nocturne-image/setup_config.sh pi@raspberrypi.local:/home/pi/

# Transfer image_config.sh to Raspberry Pi
$ scp /path/to/nocturne-image/image_config.sh pi@pi@raspberrypi.local:/home/pi/

# Ssh into Raspberry Pi
$ ssh pi@pi@raspberrypi.local

# Make setup_host.sh executable
$ chmod +x /home/pi/setup_host.sh

# Execute setup_host.sh
$ sudo ./setup_host.sh

# Reboot Raspberry Pi
$ reboot
```

Connect Car Thing to your Raspberry Pi, download and install [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/), open the app and create a new connection with the VNC Server Address of `raspberrypi.local` and the port `5900`. Input `superbird` as the password.

Right click the connection, navigate to `Properties`, then `Expert`, and set `Quality` to `High`, and ensure that `RelativePtr` is set to `False`.

Login to Spotify on the Car Thing using VNC Viewer.

### macOS

#### Raspberry Pi Setup

Download and open [Raspberry Pi Imager](https://downloads.raspberrypi.org/imager/imager_latest.dmg), select Raspberry Pi OS Lite (64-bit), select "Edit Settings", check "Set hostname", check "Set username and password" (set a password), check "Configure wireless LAN", (enter your network's SSID and password), check "Set local settings". Open the Services tab, enable SSH, and use password authentication. Write the configured OS to your microSD card and insert it into your Raspberry Pi.

#### Flashing Process

If you haven't already, download [superbird-tool](https://github.com/bishopdynamics/superbird-tool) and run the setup process detailed [here](https://github.com/bishopdynamics/superbird-tool?tab=readme-ov-file#supported-platforms).

Download and unzip [debian_v1.0_2024-10-08.tar.gz](TBD), connect Car Thing to your computer in USB Mode (hold preset buttons 1 and 4 while connecting), and run the following from your command line:

```bash
# Go into the superbird-tool repository
$ cd /path/to/superbird-tool-main

# Find device
$ /opt/homebrew/bin/python3 superbird_tool.py --find_device

# Flash Nocturne image
$ /opt/homebrew/bin/python3 superbird_tool.py --restore_device /path/to/debian_v1.0_2024-10-08

# Disable charger check
$ /opt/homebrew/bin/python3 superbird_tool.py --disable_charger_check
```

Connect your Raspberry Pi to your computer and run the following from your command line:

```bash
# Clone this repository
$ git clone https://github.com/brandonsaldan/nocturne-image

# Transfer setup_host.sh to Raspberry Pi
$ scp /path/to/nocturne-image/setup_config.sh pi@pi@raspberrypi.local:/home/pi/

# Transfer image_config.sh to Raspberry Pi
$ scp /path/to/nocturne-image/image_config.sh pi@pi@raspberrypi.local:/home/pi/

# Ssh into Raspberry Pi
$ ssh pi@pi@raspberrypi.local

# Make setup_host.sh executable
$ chmod +x /home/pi/setup_host.sh

# Execute setup_host.sh
$ sudo ./setup_host.sh

# Reboot Raspberry Pi
$ reboot
```

Connect Car Thing to your Raspberry Pi, download and install [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/), open the app and create a new connection with the VNC Server Address of `raspberrypi.local` and the port `5900`. Input `superbird` as the password.

Right click the connection, navigate to `Properties`, then `Expert`, and set `Quality` to `High`, and ensure that `RelativePtr` is set to `False`.

Login to Spotify on the Car Thing using VNC Viewer.

### Linux

#### Flashing Process

If you haven't already, download [superbird-tool](https://github.com/bishopdynamics/superbird-tool) and run the setup process detailed [here](https://github.com/bishopdynamics/superbird-tool?tab=readme-ov-file#supported-platforms).

Download and unzip [debian_v1.0_2024-10-08.tar.gz](TBD), connect Car Thing to your computer in USB Mode (hold preset buttons 1 and 4 while connecting), and run the following from your command line:

```bash
# Go into the superbird-tool repository
$ cd /path/to/superbird-tool-main

# Find device
$ sudo python3 superbird_tool.py --find_device

# Flash Nocturne image
$ sudo python3 superbird_tool.py --restore_device /path/to/debian_v1.0_2024-10-08

# Disable charger check
$ sudo python3 superbird_tool.py --disable_charger_check

# Clone this repository
$ git clone https://github.com/brandonsaldan/nocturne-image

# Go into the nocturne-image repository
$ cd /path/to/nocturne-image

# Make setup_host.sh executable
$ chmod +x /home/pi/setup_host.sh

# Execute setup_host.sh
$ sudo ./setup_host.sh
```

Connect Car Thing to your computer, download and install [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/), open the app and create a new connection with the VNC Server Address of `raspberrypi.local` and the port `5900`. Input `superbird` as the password.

Right click the connection, navigate to `Properties`, then `Expert`, and set `Quality` to `High`, and ensure that `RelativePtr` is set to `False`.

Login to Spotify on the Car Thing using VNC Viewer.

## Download

You can [download](https://github.com/brandonsaldan/releases/TBD) the latest flashable version of Nocturne for Windows, macOS and Linux.

## Credits

This software was made possible only through the following individuals and open source programs:

- [Benjamin McGill](https://www.linkedin.com/in/benjamin-mcgill/)
- [shadow](https://github.com/68p)
- [bishopdynamics & superbird-debian-kiosk](https://github.com/bishopdynamics/superbird-debian-kiosk)

## Related

[nocturne](https://github.com/brandonsaldan/nocturne) - The web application that this Debian image runs

## License

MIT

---

> [brandons.place](https://brandons.place/) &nbsp;&middot;&nbsp;
> GitHub [@brandonsaldan](https://github.com/brandonsaldan) &nbsp;&middot;&nbsp;
> Twitter [@brandonsaldan](https://twitter.com/brandonsaldan)

