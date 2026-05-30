## OptiPlex 3020 Hackintosh EFI (Sequoia‑capable)

### 1. Why this EFI exists
People keep saying “the OptiPlex 3020 Hackintosh EFI already exists.”  
That is incorrect in any meaningful technical sense.

The existing public EFI is stuck on **OpenCore 0.7.4**, which limits macOS support to **Big Sur or Monterey**.  
It cannot properly support Ventura, Sonoma, or Sequoia.

This EFI is built on a modern OpenCore version and **supports up to macOS Sequoia**.

---

### 2. SMBIOS is mandatory
The config.plist in this EFI ships with **blank SMBIOS fields**.

If you try to boot without generating your own SMBIOS, you will get errors such as:

- “OC: Device ID not allowed”
- “Invalid PlatformInfo”
- “Missing serial number”

To avoid this, you must use **genSMBIOS** to generate:

- Serial Number  
- MLB  
- System UUID  

If you change the macOS version or SMBIOS model, regenerate SMBIOS to avoid conflicts.

---

### 3. Supported macOS versions
- Big Sur — supported  
- Monterey — supported  
- Ventura — supported  
- Sonoma — supported  
- Sequoia — supported (tested on OptiPlex 3020 SFF)  
- Tahoe — not supported yet  
  - Dortania has not released stable Tahoe support  
  - Debug builds may work, but not recommended

When Dortania releases stable Tahoe support, a Tahoe‑compatible EFI will be released.

---

### 4. USB mapping requirements
This EFI is designed for the **OptiPlex 3020 SFF** only.

The USB map kext must match the SFF port layout.  
Use the USB map from this repository:

[https://github.com/varszegimarcell/Optiplex-3020-Hackintosh-OpenCore](https://github.com/varszegimarcell/Optiplex-3020-Hackintosh-OpenCore)

If you use MT or Micro models, the USB map will not match and the system will fail to boot or lose USB functionality.

If needed, you can regenerate your own map using **USBMap**.

---

### 5. GPU support
- Intel HD Graphics 4600 (iGPU) — fully supported  
- Dedicated GPUs — require manual config.plist adjustments  
  - DeviceProperties  
  - WhateverGreen settings  
  - Correct PCI paths

If you plan to use a dGPU, expect to modify the EFI.

---

### 6. Summary
- This EFI is modern and supports macOS up to Sequoia  
- SMBIOS must be generated before first boot  
- USB map is SFF‑specific  
- iGPU is supported out of the box  
- dGPU requires manual configuration  
- Tahoe is not supported until Dortania releases stable guidance
