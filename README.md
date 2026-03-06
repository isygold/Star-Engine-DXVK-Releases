# STAR ENGINE: DXVK v2.7.1 (Adreno Optimized)
### High-Performance DXVK Fork for Android Emulation

STAR ENGINE is a specialized performance modification of DXVK v2.7.1 designed specifically for Qualcomm Adreno GPUs in mobile/Android environments (Star Emulator, Winlator, Mobox). This version focuses on eliminating driver overhead and preventing command buffer overflows common in mobile gaming.

---

## 🚀 Key Technical Features

* **Dynamic-State-Aware Bind-Skip**: Reduces CPU overhead by skipping redundant vkCmdBindPipeline calls unless dynamic state (viewports/scissors) has changed.
* **Mid-Frame Command Flushing**: Automatically flushes the Vulkan command list after a configurable number of draw calls. This is a critical fix to prevent Adreno driver crashes during intensive rendering.
* **Android-Native Storage Support**: Intelligent configuration loading from common Android paths for easier setup on mobile devices.
* **Hardware Auto-Detection**: The engine automatically detects Adreno hardware to activate internal optimizations without manual user intervention.

---

## 🛠️ Installation & Setup

### Method 1: Star Emulator (Recommended)
1. Open Star Emulator.
2. Navigate to the "Contents" menu option.
3. Install the "dxvk-2.7.1.wcp" file.

### Method 2: Manual Config (Plug-and-Play)
Place your "starengine.ini" or "dxvk.conf" in one of the following supported paths:
1. /storage/emulated/0/starengine.ini
2. /storage/emulated/0/Download/starengine.ini
3. /storage/emulated/0/Winlator/starengine.ini
4. /storage/emulated/0/Android/data/[package_name]/files/starengine.ini

### Advanced Optimization (Environment Variables)
To force-activate specific StarEngine features, use the following:
* Name: DXVK_CONFIG_FILE
* Value: starengine.enabled=1; starengine.drawThreshold=150; starengine.bindSkip=1

*Name:DXVK_CONFIG_FILE
*Value: the value should be the directory where your dxvk.conf file is found in your device (if you choose the wcp file install method
---

## ⚙️ Configuration Tuning
You can modify the "DrawThreshold" value in your config file to find the perfect balance between stability and smooth gameplay:
* Recommended for Star Emulator: 150 - 300.
* DrawThreshold = 150 (Default / Stable).
* Higher values may increase performance but could lead to graphical glitches or driver crashes depending on your GPU. 

Note: The HUD name for this DXVK fork is different as listed here but performance and stability remains the intact!

## 📜 Credits & License
* Lead Developer: ISYGOLD
* Base Project: DXVK (Original by doitsujin) v2.7.1
* License: Distributed under the zlib/libpng license.

> NOTE FOR DEVELOPERS: This repository currently hosts compiled binaries and configuration documentation. Source code patches (dxvk_context.cpp and dxvk_context.h) are scheduled for release following the initial public testing phase.
