# Hackintosh-B550
Note : AMD Laptops and AMD iGPU is unsupported
Note2 : This is only for Ryzen CPUs

Hackintosh EFI for AMD Ryzen 3600 and B550 Motherboard
I just created this to backup my EFI, I highly recommend you to follow the [dortania guide](https://dortania.github.io/OpenCore-Install-Guide/) and make the efi yourself. 
If you still want to use this, change the REPLACE Section on config.plist.

# Things to Replace/Change

##ACPI 

- Disable SSDT-GPU-DISABLE.aml and SSDT-SSD-DISABLE.aml (Set Enabled to False)
- If you are not using B550 or A520, Disable SSDT-CPUR.aml (Set Enabled to False)

##Booter

###Quirks

 - Set SetupVirtualMap to True if not using X570, B550, A520, TRx40 Motherboards and X470 and B450 Motherboards with late 2020 BIOS updates
