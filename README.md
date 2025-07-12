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
| Integrated Graphics | Intel® UHD Graphics 520                     |
| Monitor             | FHD 1920x1080 (14.0 inch)                   |
| Sound Card          | Conexant CX20724                            |
| Wireless Card       | Intel® Wireless-AC 8260 802.11b/g/n/ac      |
| Ethernet/LAN        | Intel I219-LM PCI-E Gigabit Ethernet        |
| Card Reader         | Realtek RTS522A PCI-E Express card reader   |
| Touchpad            | Synaptics SMBus                             |

# Supported MacOS Version
- Sequoia 15.x.x (tested)
- Require [Heliport](https://github.com/OpenIntelWireless/HeliPort) for WiFi
- Initial Setup requires Internet via ethernet

## Working

- Intel UHD 520 Acceleration
- CPU Power Management
- Battery Status / Time
- Intel Wireless via Heliport
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

## Not Working

- IGPU Power Management (Currently using Host Preemptive)
- Apple GUC firmware
- Bluetooth BCM_4350C2
- Sleep/Wakeup & Instant Wake
- Screen LID sleep
- DRM (No HD playback on Netflix etc.)
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

## OpenCore

- OpenCore v1.0.4 (Release)

## ACPI Patch list

- SSDT-EC: Embedded Controller fix
- SSDT-PLUG-DRTNIA: Power Management Fix
- SSDT-PNLF: Brightness Fix
- SSDT-USBX: Embedded Controller fix
- SSDT-XOSI: Trackpad improvements

## Screenshots

| About this Mac                                                                                                | neofetch                                                                                                      |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| <img width="1920" height="1080" alt="Screenshot 2025-07-12 at 8 51 58 AM" src="https://github.com/user-attachments/assets/235a5584-b639-448e-b461-c73951fbb202" /> | <img width="1920" height="1080" alt="Screenshot 2025-07-12 at 8 52 23 AM" src="https://github.com/user-attachments/assets/52b87520-35c7-4b80-a07e-0d6e15f3b1d6" /> |

## Quick Installation

- Follow [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) and create a bootable macOS recovery USB
- Download the EFI and place it onto your USB drive
- Boot to OpenCore and setup your disk in Disk Utility
- The system is expected to reboot 4-5 times in total.

## Dualbooting Notes

- To install along side Windows make sure you have a GPT formatted disk, resize your Windows partition using tools such as Easeus Partition Master then while in macOS Disk Utility, make the unallocated space into APFS
- I also left a 500MB unallocated space for an EFI partition using gparted on Linux earlier I set the ESP / boot flags
- Finally copy the EFI from the repo to your disk EFI partition that you created and boot from it with the F9 key

## Credits

- @GeantW0rld Original Repo author [Suppport](https://www.buymeacoffee.com/geantworld)
- @1Revenger1 for ECEnabler
- @acidanthera for bootloader, VirtualSMC, NVMeFix, Lilu and other kexts
- @Apple for macOS
- @dortania for guides
- @itlwm for WiFi & Bluetooth
- @SkyrilHD for massive help and tips / fixes
- @TECHNIKVERBOT for Monterey patches
- @USBToolBox Team for USB mapping
- @Voodoo Team for TrackPad
