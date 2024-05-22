# OC-B590-20206
OpenCore (v. 0.9.2) config for Lenovo B590 (20206). Tested with 10.8.5 Mountain Lion ~~but may work on later versions too~~.

## Setup
1. Generate `MacBookPro9,2` SMBIOS and put it into config.plist
3. Format your USB stick
   1. Open Disk Utility
   2. Press Cmd+2 (or View -> Show all devices)
   3. Format USB stick in HFS+ (Mac OS Extended (Journaled)) with GUID partition map.
4. Download Mountain Lion 10.8.5 (I used this one https://archive.org/details/install-os-x-mountain-lion.app-10.8.4-10.8.5)
5. Create bootable USB drive
   1. If you are going to install 10.8
      1. Right-click on Install OS X Mountain Lion.app
      2. Click Show Package Contents
      3. Go to Contents/SharedSupport
      4. Double-click InstallESD.dmg to mount it
      5. Restore "Mac OS X Install ESD" to your USB drive
   2. If you are going to install 10.9+
      1. Open Terminal
      2. `/Applications/Install macOS _yourversion_.app/Contents/Resources/createinstallmedia --volume _drag_your_usb_drive_here_ --applicationpath /Applications/Install macOS _yourversion_.app`
6. Mount EFI partition (use [MountEFI](https://github.com/corpnewt/MountEFI) utility for that)
7. Put `EFI` directory in EFI partition
8. Unmount your USB stick & reboot
9. Enter BIOS
   1. On `Config` tab go to `USB` section and set `USB 3.0 Mode` to `Disabled`
   2. On `Config` tab go to `Power` section and set everything to `Enabled`
   3. On `Config` tab go to `Serial ATA (SATA)` section and set `SATA Controller Mode Option` to `AHCI`
   4. On `Config` tab go to `CPU` section and set everything to `Enabled`
   5. On `Security` tab go to `Virtualization` section and set `Intel (R) Virtualization Technology` to `Enabled`
   6. On `Security` tab go to `Secure Boot` section and set `Secure Boot` to `Disabled`
   7. On `Startup` tab set `UEFI/Legacy Boot` to `Both`
   8. On `Startup` tab (for convenience) go to `Boot` section and set your USB drive as the first device in boot priority
   9. Save & Reboot
10. Boot from your USB stick and choose installer
11. Don't forget to set date in Terminal (you can google that for your version of OS X)
12. Perform usual installation
13. Mount EFI partition of your system drive
14. Copy `EFI` directory on EFI partition of your system drive

## Laptop Specifications
Lenovo B590 (20206)
- CPU: Intel Celeron 1005M
- GPU: Intel HD Graphics 2500
- RAM: 4 GB
- Ethernet: RTL8111/8168/8411 (?) - to be clarified
- Wi-Fi: Broadcom BCM43142
- PS/2 Keyboard & Trackpad
- Audio codec: Realtek ALC269 (?) - to be clarified

## Hardware support
🟢 Works
- CPU Power Management (?) - to be clarified
- USB 2.0
- Audio
- Touchpad & Keyboard

🟡 Partly
- Graphics Acceleration (it actually works but with some limitations)

🔴 Not works
- Wi-Fi
- HDMI
