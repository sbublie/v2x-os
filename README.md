# V2X-OS

The V2X-OS image for the Raspberry Pi can be downloaded here:

[![Download v2x-os](https://a.fsdn.com/con/app/sf-download-button)](https://sourceforge.net/projects/v2x-os/files/latest/download)

Use the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) to flash the image onto an SD-Card. 

*Tested on Raspberry Pi Model 3 B+*

# Setup

### Required Hardware:

- Cohda Mk5 OBU with antenna and corresponding power cable
- 12V power supply for Cohda OBU (e.g. 12V battery)
- Raspberry Pi, SD card and power supply
- Ethernet cable
- PC for setup
- Client OBU (Windows or Android device)

### Raspberry Pi Configuration

- Wi-Fi SSID: _ITSRouter_
- Wi-Fi password: itsrouter
- IP address: 192.168.1.1
- SSH user: pi
- SSH password: raspberry

### Cohda OBU Configuration

- IP address: fe80::6e5:48ff:fe20:5b58%eth0
- SSH user: user
- SSH password: user

## Step-by-Step Setup Guide

### **Hardware Connection**

_Do not power on the Cohda OBU before connecting the antenna!_

**1.** Connect all three antenna cables to the Cohda OBU.

**2.** Connect the Raspberry Pi and the Cohda OBU using the Ethernet cable.

**3.** Power on the Raspberry Pi by using the micro USB power supply or a power bank.

**4.** Power on the Cohda OBU by connecting it to the power supply with the enclosed battery cable. Please check the polarity!

### **Raspberry Pi**

**1.** Connect the PC to the Raspberry Pi's Wi-Fi network. SSID: `ITSRouter` Password: `itsrouter`

**2.** Establish a ssh connection to the Raspberry Pi from the terminal:

```bash
ssh pi@192.168.1.1
```

Password: `raspberry`

**3.** Run the V2X-Server with:

```bash
./v2x_server
```

To start the server with sample data use:

```bash
./v2x_server debug
```

### **Cohda OBU**

**1.** Establish a ssh connection to the Raspberry Pi from the terminal:

```bash
ssh pi@192.168.1.1
```

Password: `raspberry`

**2.** Connect to the Cohda OBU using:

```bash
ssh user@fe80::6e5:48ff:fe20:5b58%eth0
```

Password: `user`

**3.** To initiate the UDP package redirection to the Raspberry Pi use:

```bash
/opt/cohda/test/runtest_monitor.sh 180 192.168.1.1 target
```

The program is now running and can be cancelled with _Ctrl + C_.

### **Client**

**1.** Connect the client device to the Raspberry Pi's Wi-Fi network.

**2.** Open the V2X-Pilot app. If the app asks for an IP address enter `192.168.1.1` and hit confirm.
