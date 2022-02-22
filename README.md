# dell-vostro-15-3568-hackintosh
Special thanks to:
- [acidanthera](https://github.com/acidanthera) for making this Hackintosh possible in the first place
- [dortania people](https://github.com/orgs/dortania/people) for the [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [dreamwhite](https://github.com/dreamwhite) for their [CFG Lock disabling guide](https://github.com/dreamwhite/bios-extraction-guide/tree/master/Dell)
- [doanhxd](https://github.com/doanhxd) for [their Vostro 15-3568 setup](https://github.com/doanhxd/Dell-Vostro-3568-Hackintosh), mine is partly based on it.
- [Mili](https://www.youtube.com/channel/UCVh47EKH9VLresRqiYi9txw) for the wallpaper and the goated music :pray:

# Intro
![Screen Shot 2022-02-22 at 20 02 49](https://user-images.githubusercontent.com/92439990/155137865-0253dddf-e0a0-4390-9ed3-c7bde36adc6a.png)


|              | Version         |
|-------------:|:----------------|
| ``OpenCore`` | 0.7.8 (RELEASE) |
| ``Monterey`` | 12.2.1 (21D49)  |

(This config works with macOS 11 too)

# Disclaimer
- I don't care what you do with it, except for commercial purposes. Refer to [Psystar's case](https://en.wikipedia.org/wiki/Psystar_Corporation).
- Reminder that this is only a base for your OpenCore setup, it is strongly recommended that you follow the entire OpenCore guide [here](https://dortania.github.io/OpenCore-Install-Guide/)
- There will be differences probably even for the same line of machine, however if you're feeling lazy I guess you can just copy the config, just remember to add in information such as the MLB or the ROM in `PlatformInfo`.

# Issues and notes
- Sleep
  - Trackpad/mouse wake doesn't work
  - Sometimes require a keyboard+power combo to wake up. Darkwake issue that I haven't got around to fixing.
- Brightness is controlled by Fn+S and Fn+B rather than Fn+F11 and Fn+F12
- ~~Moving the cursor with the trackpad works, but I don't know how are you supposed to click :moyai:~~ Just put in a battery smh my head
- Don't use case-sensitive APFS if you want to use Steam or Adobe tools. 
  - If you've selected a case-sensitive file system, it is still possible to run Steam with [this guide](https://davejansen.com/how-to-run-steam-when-your-macos-drive-is-case-sensitive/), but Adobe apps can't be installed.

# Pre-install tasks
- BACK UP YOUR STUFF, ESPECIALLY YOUR SSH KEYS, DON'T BE THIS GUY
![Screen Shot 2022-01-23 at 17 40 27](https://user-images.githubusercontent.com/92439990/150674757-954e820a-5d5f-4d38-a09a-d2bf66403812.png)
- Keep your DSDT table dump somewhere safe, it's less convenient to dump on macOS

# Post-install tasks
Refer to [OpenCore Post-Install guide](https://dortania.github.io/OpenCore-Post-Install) for more detail.

- Copy the EFI from your OpenCore USB over to your EFI partition (no shit)
- Fix sleep. I have already included a FixShutdown SSDT, but if this does not work, you'll have to build one yourself.
- [Disable CFG Lock](https://github.com/dreamwhite/bios-extraction-guide/tree/master/Dell#step-4-setting-cfg-lock-to-0x00): my offset is `0x4C7`, found on v3.11.0, though my BIOS is significantly older (v2.6.0).

# Hardware

|                                           | Specifications                                                                | macOS Big Sur Compatibility                                                                                                                   |
| ----------------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| ``Chipset``                               | Intel Kaby Lake                                                               |                                                                                                                                               |
| ``CPU``                                   | Intel Core i7-7500U Processor, 2 Cores / 4 Threads, 2.7Hz / 3.5GHz, 4MB Cache |                                                                                                                                               |
| ``Memory``                                | 8GB dual-channel DDR4-2133MHz, up to 16GB                                     |                                                                                                                                               |
| ``GPU``                                   | Intel HD Graphics 620                                                         |                                                                                                                                               |
| ``dGPU``                                  | AMD Radeon HD 8550M/R5 M230 (2GB GDDR3 VRAM)                                  | Not supported. Disabled with boot-args `-wegnoegpu`                                                                                           |
| ``Storage``                               | Kingmax SATA SSD 240GB + 1TB HDD                                              |                                                                                                                                               |
| ``Screen``                                | 15.6" Full HD 60Hz, 1920 x 1080 TN                                            |                                                                                                                                               |
| ``Webcam``                                | Integrated HD Webcam                                                          |                                                                                                                                               |
| ``Ethernet``                              | RJ45 RTL8111 Realtek Ethernet                                                 |                                                                                                                                               |
| ``WiFi``                                  | Intel Wireless-AC 3165                                                        | Using [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases)                                                                |
| ``Bluetooth``                             | Intel                                                                         | Using [IntelBluetoothFirmware](https://openintelwireless.github.io/IntelBluetoothFirmware). |
| ``Input & Output``                        | USB 3.0 (USB-A) x2 + USB 2.0 (USB-A) x1<br>HDMI 1.4<br>VGA                    | No issues, you can build your own mapping with [USBToolBox](https://github.com/USBToolBox/tool) on Windows if the provided kext doesn't work  |
| ``Soundboard``                            | Realtek ALC256 (ALC3246)                                                      |                                                                                                                                               |
| ``Battery``                               | 40Wh Dell battery                                                             | About 2 hours with bad power management                                                                                                                               |
| ``Keyboard``                              | -                                                                             |                                                                                                                                               |
| ``Touchpad``                              | Dell Touchpad                                                                 | No issues. ACPI should be patched to enable gesture                                                                                           |
| ``Dimensions``<br>``Weight``<br>``Power`` | 23.65mm x 260mm x 380mm<br>2.29kg<br>65W Power Adapter                        | ACPI patches won't help with these                                                                                                            |
