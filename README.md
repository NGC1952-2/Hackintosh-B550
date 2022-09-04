# Hackintosh-B550
Hackintosh EFI for AMD Ryzen 3600 and B550 Motherboard
This EFI is not for AMD FX/AMD Laptops and Old AMD CPUs.
I just created this to backup my EFI, I highly recommend you to follow the [dortania guide](https://dortania.github.io/OpenCore-Install-Guide/) and make the efi yourself. 
If you still want to use this, change the REPLACE Section on config.plist.

# Things to Replace/Change

I highly recommend using Corpnewt's Propertree to edit your config.plist.

## ACPI 

- Disable SSDT-GPU-DISABLE.aml and SSDT-SSD-DISABLE.aml (Set Enabled to False)
- If you are not using B550 or A520, Disable SSDT-CPUR.aml (Set Enabled to False)

## Booter

#### Quirks

 - Set SetupVirtualMap to True if not using X570, B550, A520, TRx40 Motherboards and X470 and B450 Motherboards with late 2020 BIOS updates
 - Set ResizeAppleGpuBars to -1 if your Motherboard does not support Resizable BAR 
 - If you have a Ryzen ThreadRipper CPU, enable Devirtualizemmio and follow [this guide](https://dortania.github.io/OpenCore-Install-Guide/extras/kaslr-fix.html).
 
## Kernel

#### Add

-- I used VoodooHDA instead of AppleALC, but if you are going to use AppleALC, put it on EFI/OC/Kexts and OC Snapshot.

#### Patch

-- Modify the Replace Value on 3 patches called algrey - Force cpuid_cores_per_package with the physical core count of your CPU in hexadecimal.

B8000000 0000 => B8 <core count> 0000 0000
BA000000 0000 => BA <core count> 0000 0000
BA000000 0090 => BA <core count> 0000 0090

2 Core	02

4 Core	04

6 Core	06

8 Core	08

12 Core	0C

16 Core	10

24 Core	18

32 Core	20

64 Core	40

## Misc

#### Security 
 
Set SecureBootModel to Default if you are not using NVIDIA Web Drivers

## NVRAM

#### Add

###### 7C436110-AB2A-4BBB-A880-FE41995C9F82

remove amfi_get_out_of_my_way=0x1 and ipc_control_port_options=0 if you don't need to disable AMFI.
add alcid=1 if using AppleALC

## PlatformInfo

Generate an SMBIOS using Corpnewt's GenSMBIOS and copy the Vaules to config.plist. 

The Type part gets copied to Generic -> SystemProductName.

The Serial part gets copied to Generic -> SystemSerialNumber.

The Board Serial part gets copied to Generic -> MLB.

The SmUUID part gets copied to Generic -> SystemUUID.

The Apple ROM part gets copied to Generic -> ROM.

