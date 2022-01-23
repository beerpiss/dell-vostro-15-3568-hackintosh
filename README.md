# dell-vostro-15-3568-hackintosh
Thanks to [doanhxd](https://github.com/doanhxd) for [their Vostro 15-3568 setup](https://github.com/doanhxd/Dell-Vostro-3568-Hackintosh), mine is partly based on it.

# Intro

![About this Mac](https://user-images.githubusercontent.com/92439990/150672996-0018f74e-0b67-4c6c-b3b6-0a96460ad7eb.png)

| | Version |
| ---: | :--- |
| ``OpenCore`` | 0.7.7 (RELEASE) |
| ``Big Sur`` | 11.6.2 (20G314) |

# Disclaimer
- Reminder that this is only a base for your OpenCore setup, it is strongly recommended that you follow the entire OpenCore guide [here](https://dortania.github.io/OpenCore-Install-Guide/)
- There will be differences probably even for the same line of machine, however if you're feeling lazy I guess you can just copy the config, just remember to add in information such as the MLB or the ROM in `PlatformInfo`.

# Notes
Don't use case-sensitive APFS if you want to use Steam or Adobe tools.

# Post-install tasks
- Copy the EFI from your OpenCore USB over to your EFI partition (no shit)
- Fix sleep. I have already included a FixShutdown SSDT, but if this does not work, you'll have to build one yourself.
- Disable CFG Lock (my offset is `0x4C7`, found on v3.11.0, though my BIOS is older).

# Hardware

| | Specifications | macOS Big Sur Compatibility |
| ---: | :--- | :--- |
| ``Chipset`` | Intel Kaby Lake |  |
| ``CPU`` | Intel Core i7-7500U Processor, 2 Cores / 4 Threads, 2.7Hz / 3.5GHz, 4MB Cache |  |
| ``Memory`` | 8GB dual-channel DDR4-2133MHz, up to 16GB | |
| ``GPU`` | Intel HD Graphics 620 |  |
| ``dGPU`` | AMD Radeon HD 8550M/R5 M230 (2GB GDDR3 VRAM) | Not supported. Disabled with boot-args `-wegnoegpu` |
| ``Storage`` | Kingmax SATA SSD 240GB + 1TB HDD |  |
| ``Screen`` | 15.6" Full HD 60Hz, 1920 x 1080 TN | |
| ``Webcam`` | Integrated HD Webcam |  |
| ``Ethernet`` | RJ45 RTL8111 Realtek Ethernet |  |
| ``WiFi`` | Intel Wireless-AC 3165 | Using [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) |
| ``Bluetooth`` | Intel | Using [IntelBluetoothFirmware](https://openintelwireless.github.io/IntelBluetoothFirmware). AirDrop may be a little finnicky, but should work |
| ``Input & Output`` | USB 3.0 (USB-A) x2 + USB 2.0 (USB-A) x1 | No issues, you can build your own mapping with [USBToolBox](https://github.com/USBToolBox/tool) on Windows if the provided kext doesn't work |
| - | HDMI 1.4 |  |
| - | VGA |  |
| ``Soundboard`` | Realtek ALC256 (ALC3246) |  |
| ``Battery`` | I removed it | I don't know |
| ``Keyboard`` | - |  |
| ``Touchpad`` | Dell Touchpad | No issues. ACPI should be patched to enable gesture |
| ``Dimensions`` | 23.65mm x 260mm x 380mm | ACPI patches won't help with these |
| ``Weight`` | 2.29 kg | |
| ``Power`` | 65W Power Adapter | |


