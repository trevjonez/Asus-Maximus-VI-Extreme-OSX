## Asus-Maximus-VI-Extreme-OSX

Asus M6E SSDT source dsl files and other config info for OSX

### Custom SSDT for USBInjectAll.kext

Based on the [tonymacx86 guide](https://www.tonymacx86.com/threads/guide-creating-a-custom-ssdt-for-usbinjectall-kext.211311/) using [RehabMan/OS-X-USB-Inject-All](https://github.com/RehabMan/OS-X-USB-Inject-All)

[SSDT-UIAC-M6E.dsl](/SSDT-UIAC-M6E.dsl)

Be sure to read the readme and get the `EC0 to EC`, `EHC1 to EH01`, `EHC2 to EH02` and `XHC1 to XHC` DSDT patches in `config.plist`

I also ended up needing to set `DropOEM_DSM.Usb = true` before anything would show under EH02 in IORegistryExplorer.

TODO: Possible some required DSDT section fixes required to get the EH02 subs to show correctly. Need to start removing one at a time to see how much we can skip on.

![Port Detection Notes](/M6E-PortDetectionNotes.png)

### Cpu Power Management SSDT

Based on the [tonymacx86 guide](https://www.tonymacx86.com/threads/quick-guide-to-generate-a-ssdt-for-cpu-power-management.177456/) using [Piker-Alpha/ssdtPRGen.sh](https://github.com/Piker-Alpha/ssdtPRGen.sh)

[SSDT-CpuPm-4790K.dsl](/SSDT-CpuPm-4790K.dsl)

### Kexts etc...

For UsbInjectAll to work and likely other stuff, install the following kexts:
`FakePCIID.kext` and `FakePCIID_XHCIMux.kext` from [RehabMan/OS-X-Fake-PCI-ID](https://github.com/RehabMan/OS-X-Fake-PCI-ID)

Sound and Wifi/BT need `Lilu.kext` from [acidanthera/Lilu](https://github.com/acidanthera/Lilu)

Sound needs `AppleALC.kext` from [acidanthera/AppleALC](https://github.com/acidanthera/AppleALC) and in `config.plist` `Devices.Audio.Inject = 1`

Wifi and Bluetooth need `AirportBrcmFixup.kext`, `BrcmFirmwareRepo.kext`, `BrcmPatchRAM2.kext` based on the [tonymacx86 guide](https://www.tonymacx86.com/threads/broadcom-wifi-bluetooth-guide.242423/#post-1664577)

I have had the best luck installing kexts to /L/E and made no attempt to use clover to load them as it has not been sufficient in the past for Wifi/BT.