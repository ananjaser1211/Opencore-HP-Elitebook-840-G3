# Opencore-HP-EliteBook-840-G3

<B>OpenCore Hackintosh - HP Elitebook 840 G3</B>

## Specifications

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Computer model      | HP Elitebook 840 G3                         |
| CPU                 | Intel Core i5-6200U                         |
| Memory              | 8GB/4GB DDR4 SK Hynix 2133MHz               |
| SSD                 | Samsung NVME SSD 970 EVO 500GB (PM981)      |
| HDD                 | Toshiba MQ02ABF050H 500GB                   |
| Integrated Graphics | Intel® HD Graphics 520                      |
| Monitor             | FHD 1920x1080 (14.0 inch)                   |
| Sound Card          | Conexant CX20724                            |
| Wireless Card       | Intel® Wireless-AC 8260 802.11b/g/n/ac      |
| Ethernet/LAN        | Intel I219-LM PCI-E Gigabit Ethernet        |
| Card Reader         | Realtek RTS522A PCI-E Express card reader   |
| Touchpad            | Synaptics SMBus                             |

# Supported MacOS Version
- Sequoia 15.x.x (tested)
- Require [Heliport](https://github.com/OpenIntelWireless/HeliPort) for WiFi
- Initial Setup requires Internet via ethernet if using offline installers

## Working

- iGPU acceleration (using HD 620 device-id for Ventura and newer)
- CPU Power Management
- Battery Status / Time
- Intel Wireless via Heliport
- Intel Bluetooth
- Ethernet LAN
- NVMe Storage
- Realtek Audio & F7/F8 keys
- Audio Combo Jack
- Keyboard & Media/Function Keys
- Trackpad & Gestures support
- USB Type-A & Type-C ports
- HP Webcam
- Screen Brightness & F2/F3 Keys
- And pretty much everything not listed below
- DP (& HDMI Adapter)
- VGA Output
- Sleep/Wakeup & Instant Wake
- Screen LID sleep

## Not Working

- Apple GUC firmware (Currently using Host Preemptive)
- DRM (No HD playback on Netflix etc. using Safari)
- SDXC Card Reader (Not supported in MacOS Sequoia)

# Bios Settings
* Security -> Intel Software Guard Extensions (SGX) -> Disable
* Advanced -> Boot Options -> Uncheck “Fast Boot”
* Advanced -> Boot Options -> Check “UEFI Boot Order”
* Advanced -> Boot Options -> Uncheck “Legacy Boot Order”
* Advanced -> Secure Boot Configuration -> Configure Legacy Support and Secure Boot -> Legacy Support Disable and Secure Boot Disable
* Advanced -> System Options ->  Check “Hyperthreading”
* Advanced -> System Options -> Check “Virtualization Technology (VTx)”
* Advanced -> System Options -> Uncheck “Virtualization Technology for Directed I/O (VTd)”
* Advanced -> Built-In Device Options -> Video memory size -> 64MB or anything higher
* Advanced -> Wake On LAN ->  Set “Disabled” otherwise sleep will not work

## OpenCore

- OpenCore v1.0.4 (Release)

## ACPI Patch list

- SSDT-EC: Embedded Controller fix
- SSDT-PLUG: Power Management Fix
- SSDT-PNLF: Brightness Fix
- SSDT-USBX: Embedded Controller fix
- SSDT-XOSI: Trackpad improvements
- SSDT-GPRW: Instant wake fix
- SSDT-HP-FixLidSleep: Screen LID Sleep Fix

## Kexts

| Kext                                                                                  | Version | Details | Usage                                                           |
| ------------------------------------------------------------------------------------- | ------- | ------- | --------------------------------------------------------------- |
| [Itlwm](https://github.com/OpenIntelWireless/itlwm)                                   | v2.3.0  | Release | Intel Wi-Fi Adapter Kext for macOS                              |
| [AppleALC](https://github.com/acidanthera/AppleALC)                                   | v1.9.5  | Release | Native macOS HD audio for not officially supported codecs       |
| [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM)                          | v2.7.1  | Release | Monterey Bluetooth Firmware fix-up                              |
| [ECEnabler](https://github.com/1Revenger1/ECEnabler)                                  | v1.0.6  | Release | Allows reading Embedded Controller fields over 1 byte long      |
| [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | v2.4.0  | Release | Intel Bluetooth Drivers for macOS                               |
| [IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)         | v2.4.0  | Release | Intel Bluetooth Firmware Uploader                               |
| [Lilu](https://github.com/acidanthera/Lilu)                                           | v1.7.1  | Release | Arbitrary kext and process patching on macOS                    |
| [NVMeFix](https://github.com/acidanthera/NVMeFix)                                     | v1.1.3  | Release | Set of patches for the Apple NVMe storage driver                |
| [IntelMausi](https://github.com/Mieze/RTL8111_driver_for_OS_X)                        | v1.0.8  | Release | Intel Ethernet LAN driver for macOS                             |
| [RestrictEvents](https://github.com/acidanthera/RestrictEvents)                       | v1.1.6  | Release | Suppresses unwanted notifications in macOS                      |
| [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC)                        | v1.3.7  | Release | Battery Management For Laptops                                  |
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC)                             | v1.3.7  | Release | Improved CPU measurement                                        |
| [USBMap](https://github.com/CorpNewt/USBMap)                                          | v1.0    | Gen     | Generated USB Map                                               |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)                               | v1.3.7  | Release | Advanced Apple SMC emulator in the kernel                       |
| [VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2)                       | v2.3.7  | Release | Controller For various PS2 Gestures                             |
| [VoodooRMI](https://github.com/VoodooSMBus/VoodooRMI)                                 | v1.4.2  | Release | A port for macOS of Synaptic's RMI Trackpad driver from Linux   |
| [VoodooSMBUS](https://github.com/VoodooSMBus/VoodooRMI)                               | v3.0    | Release | VoodooRMI Extension for PS2 Trackpad                            |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen)                         | v1.7.0  | Release | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs |

## Screenshots

| About this Mac                                                                                                | neofetch                                                                                                      |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| <img width="1920" height="1080" alt="Screenshot 2025-07-12 at 8 51 58 AM" src="https://github.com/user-attachments/assets/235a5584-b639-448e-b461-c73951fbb202" /> | <img width="1920" height="1080" alt="Screenshot 2025-07-12 at 8 52 23 AM" src="https://github.com/user-attachments/assets/52b87520-35c7-4b80-a07e-0d6e15f3b1d6" /> |

## Quick Installation

- Follow [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) and create a bootable macOS recovery USB
- Download the EFI and place it onto your USB drive
- Boot to OpenCore and setup your disk in Disk Utility
- The system is expected to reboot 4-5 times in total.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro13,1

Use Xcode, [ProperTree](https://github.com/corpnewt/ProperTree) or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, UUID and ROM)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

## Dualbooting Notes

- To install along side Windows make sure you have a GPT formatted disk, resize your Windows partition using tools such as Easeus Partition Master then while in macOS Disk Utility, make the unallocated space into APFS
- I also left a 500MB unallocated space for an EFI partition using gparted on Linux earlier I set the ESP / boot flags
- Finally copy the EFI from the repo to your disk EFI partition that you created and boot from it with the F9 key

## Credits

- [@GeantW0rld](https://github.com/GeantW0rld) Original Repo author [Support](https://www.buymeacoffee.com/geantworld)
- [@TECHNIKVERBOT](https://github.com/TECHNIKVERBOT) for rebuilding EFI + Support
- [@SkyrilHD](https://github.com/SkyrilHD) for massive help and tips / fixes
- @1Revenger1 for ECEnabler
- @acidanthera for bootloader, VirtualSMC, NVMeFix, Lilu and other kexts
- @itlwm for WiFi & Bluetooth
- @dortania for guides
- @Apple for macOS
- @USBToolBox Team for USB mapping
- @Voodoo Team for TrackPad
