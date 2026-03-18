# STAR ENGINE: DXVK v2.7.1.1 (Adreno Optimized ASYNC VERSION)
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

NOTE THAT THE BIND SKIP VALUE CAN BE CHANGED BASED ON THE LEVEL OF GAME STUTTERING.
---

## ⚙️ Configuration Tuning
You can modify the "DrawThreshold" value in your config file to find the perfect balance between stability and smooth gameplay:
* Recommended for Star Emulator: 150 - 300.
* DrawThreshold = 150 (Default / Stable).
* Higher values may increase performance but could lead to graphical glitches or driver crashes depending on your GPU. 










## UPDATE LOG 2: (DXVK 2.7.1.1)

🛠️ Key Technical Features

-Dynamic-State-Aware Bind-Skip: Reduces CPU overhead by skipping redundant pipeline calls unless dynamic states (viewports/scissors) change.
-Mid-Frame Command Flushing: Automatically flushes the command list after a configurable number of draw calls to prevent Adreno driver crashes.
-Android Storage Support: Intelligent configuration loading from paths like /sdcard, /Download, and /Winlator.


Configuration & Installation(still the same as the previous installation)

------------------------------------------------------------
------------------------------------------------------------

## NOTE (FOR BIONIC VERSION USAGE): 
* The turnip version 25.1.0 as default does not properly communicate with this dxvk driver hence should not be used as it will not work! properly install the latest turnip driver that is good or compatible for your device performance. All installations and manual placing should be done before the creating a container and the drivers are to be set during installation as this ensures a clean setup! 
* Also the box 64 version is to be considered; version 0.3.6/ 0.3.6-xxxx for stability usage with this driver(this can be as a fall back for performance) versions 0.3.7/0.3.7-xxxx - 0.4.xxxx variant are recommended for better performance.( This relies greatly and depends on the Device used)
* The tests in the container will have low fps beacuse of the draw call threshold being set but will notice a very smooth frame pacing and smoother test, this applies in the game as well depending on your specific hardware device (GPUS with 6xx-7xx and 8s gen 1 too will be working good for this driver).
* You can tweak your dxvk.conf to better suit your specific game having heavy stutter and lags which help in reducing its issue, but remember to always have a copy of your previous tweaked or default dxvk.conf file incase you want to fallback to it.
* Provide log files when placing issues down it helps a lot to pinpoint the exact issues.
* The HUD name for this DXVK fork is different as listed here but performance and stability remains the intact! 

---


## 📜 Credits & License
* Lead Developer: ISYGOLD
* Base Project: DXVK (Original by doitsujin) v2.7.1
* License: Distributed under the zlib/libpng license.

> NOTE FOR DEVELOPERS: This repository currently hosts compiled binaries and configuration documentation. Source code patches (dxvk_context.cpp and dxvk_context.h) are scheduled for release following the initial public testing phase. 
