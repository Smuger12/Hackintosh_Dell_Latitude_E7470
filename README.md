**pls don't use this ~~shit~~ there is better [ones](https://osxlatitude.com/forums/topic/9179-dell-latitude-e7x70-clover-and-opencore/?do=findComment&comment=104256)**

<br>

<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

# macOS Monterey on Dell Latitude E7470 

<img align="right" src="https://imgur.com/25u1lIk.jpg" width="300">

## Introduction

<details>  
<summary><strong>Getting started</strong></summary>
</br>

**Meet the bootloader:**

- [Why OpenCore?](https://dortania.github.io/OpenCore-Install-Guide/why-oc.html)
- [Dortania's website](https://dortania.github.io)

**Recommended tools:**

- Plist editor: [ProperTree](https://github.com/corpnewt/ProperTree)
- EFI Partition Mounting Script: [MountEFI](https://github.com/corpnewt/MountEFI)

</details>

<details>  
<summary><strong>My Hardware</strong></summary>
<br>

| Model              | Dell Latitude E7470                        |
|:-------------------|:-------------------------------------------|
| Processor          | Intel Core i5-6300U                        |
| Graphics           | Integrated Intel HD Graphics 520           |
| Memory             | 8GB 2133MHz DDR4 SODIMM (Dual channel)     |
| Display            | 14" WQHD (2560x1440) with ELAN Touchscreen |
| Storage            | Sandisk 256GB M.2 SATA SSD                 |
| WLAN + Bluetooth   | Intel Dual Band Wireless-AC 8260           |
| Camera             | 1920x1080 FHD Webcam                       |
| Fingerprint Reader | No                                         |
| Soundcard          | Realtek ALC293                             |
| Keyboard           | Backlit Keyboard                           |
| Trackpad           | ALPS Touchpad                              |

</details>

## Status

<details>  
<summary><strong>What's working</strong></summary>
</br>

- [x] Intel HD 520 Graphics **`including graphics acceleration`**
- [x] All USB ports
- [x] Internal camera
- [x] WiFi using [AirportItlwm](https://github.com/OpenIntelWireless/itlwm)
- [x] Bluetooth using [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (without IntelBluetoothInjector.kext) and BlueToolFixup.kext from: [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM)
- [x] Shutdown/Reboot/Sleep/Wake
- [x] Speakers and headphones jack
- [x] Intel Gigabit Ethernet
- [x] iMessage, FaceTime, App Store
- [x] miniDP and HDMI with digital audio passthrough (If you experience cursor lags, try turning on and off one of the displays.)
- [x] Keyboard and Trackpad (two finger vertical swipes)
- [x] DRM (Works with Google Chrome. Tested with Netflix.)
- [x] SD Card Reader using [Sinetek-rtsx](https://github.com/cholonam/Sinetek-rtsx)

</details>
<details>  
<summary><strong>What's not working</strong></summary>
</br>

- [ ] [Multitouch gestures for ALPS touchpad.](https://github.com/adityabakare/macOS-Dell-Latitude-E7470/issues/1)

</details>

## Current configuration

- macOS: Monterey 12.2.1
- OpenCore: 0.7.4

## Installation

<details>
<summary><strong>Create the USB</strong></summary>
<br>

Follow the [guide on the OpenCore documentation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a USB for installation. Choose the operating system you use to create the USB and proceed with the guide. At the end of the Create USB section, OpenCore will ask us to do additional configurations. We don't need to do any of that because the `EFI` folder in this repository provides all necessary configurations we need for installation on Dell Latitude E7470.
</details>

<details>
<summary><strong>Boot and Install macOS</strong></summary>
<br>

- Plug in the USB we created to your Dell computer
- Press the Power button to turn on our computer (if you used the Dell to create the USB, shutdown the computer first) and spam `F12` key to launch boot menu and choose your USB to boot from it
- Wait and we will see the Apple icon on a black screen with a progress bar at the bottom
- Then, we will see a menu with four options. Make sure select `Disk Utility` to partition your disk appropriately and format the partition for installing macOS into `APFS`. If you are dual booting with other operating systems, an easier way would be to partition the drive beforehand as some formats like NTFS are readonly on macOS.
- Follow the installation steps and configure the preferences to your liking
- Log in to macOS and enjoy :D

</details>

## Post Installation

<details>
<summary><strong>Booting without USB</strong></summary>
</br>

You need to plug in the installation USB created previously everytime you start macOS after shutdown. If you want to boot without the USB, follow [this guide by OpenCore](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb).

</details>

<details>
<summary><strong>Fixing UK keyboard</strong></summary>
<br>

Choose layout file from [`Keyboard_Layouts`](./Keyboard_Layouts) repo directory and put it in `/Library/Keyboard Layouts` directory.
   
</details>

<details>
<summary><strong>Fixing iServices</strong></summary>

- In order to get Apple Services like App Store working, you need to generate your own SMBIOS(The included one is only for reference).

- For more information on how to do that, visit the [Dortania Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).

</details>

## Credits

- [Acidanthera](https://github.com/acidanthera) for OpenCore, Lilu and related kexts.
- [OpenIntelWireless](https://github.com/OpenIntelWireless) and others whose kexts I've used.
- [Dortania](https://dortania.github.io) for installation and other guides.
- [Aditya Bakare](https://github.com/adityabakare) - [Big Sur](https://github.com/adityabakare/macOS-Dell-Latitude-E7470)
- [Yosef-y053f01](https://github.com/y053f01) for most of the files I used.
- Everyone else who contributed to this repository directly/indirectly.
