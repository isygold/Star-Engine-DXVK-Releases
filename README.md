<img width="1152" height="768" alt="STAR-ENGINE-DXVK" src="https://github.com/user-attachments/assets/00cae1c5-0e64-44c1-adbc-2e504705cd6b" />

## STAR ENGINE: DXVK v2.7.1.1 (Adreno Optimized ASYNC VERSION)
[![Sponsor](https://img.shields.io/badge/Sponsor-%24?logo=github&style=flat)](https://github.com/sponsors/isygold)

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
* The tests in the container will have low fps beacuse of the draw call threshold being set but will notice a very smooth frame pacing and smoother test and smoother gameplay, which is the main aim of the driver, this applies in the game as well depending on your specific hardware device (GPUS with 6xx-7xx and 8s gen 1 too will be working good for this driver). If you're judging the speed based on the built-in container tests or system tools, don't trust them! They don't handle the Async paths in STAR ENGINE properly. Test with an actual game (like Tomb Raider or RE) and turn on the DXVK_HUD to make sure the engine is actually loading.
* You can tweak your dxvk.conf to better suit your specific game having heavy stutter and lags which help in reducing its issue, but remember to always have a copy of your previous tweaked or default dxvk.conf file incase you want to fallback to it.
* Provide log files when placing issues down it helps a lot to pinpoint the exact issues.
* The HUD name for this DXVK fork is different as listed here but performance and stability remains the intact!
* Make sure to avoid mistakes when inputing the environment variables as this is crucial for this version
![Screenshot_2026-03-17-09-09-29-987_com winlator cmod](https://github.com/user-attachments/assets/ef0ddc15-65cf-4c69-8345-5955534550cc)
![Screenshot_2026-03-17-11-27-08-078_com winlator cmod](https://github.com/user-attachments/assets/272e8935-f57b-4b2d-8a8e-4cc085519309)
![Screenshot_2026-03-17-11-44-38-570_com winlator cmod](https://github.com/user-attachments/assets/03765f1e-3d38-4144-96e2-75107440a3e9)
![Screenshot_2026-03-17-11-46-08-680_com winlator cmod](https://github.com/user-attachments/assets/2074f2da-7e70-4385-95d5-b9bb134f2409)

* For max performance locking use the FEXCORE and VKD3D+DXVK and DGVOODO
* ![Screenshot_2026-04-05-19-00-22-978_com winlator star](https://github.com/user-attachments/assets/313da954-6b8d-41af-a328-cc7da58b41d5)
![Screenshot_2026-04-05-19-05-21-483_com winlator star](https://github.com/user-attachments/assets/f4f580dc-e1fd-46e2-8d7a-fcd62df38bbd)
![Screenshot_2026-04-05-19-07-27-369_com winlator star](https://github.com/user-attachments/assets/aac90501-c949-43d9-a93a-9e7b24eb18ae)
![Screenshot_2026-04-05-19-22-26-530_com winlator star](https://github.com/user-attachments/assets/77ad9a68-1a70-4f77-beab-758a5de7fbaa)


---


## 📜 Credits & License
* Lead Developer: ISYGOLD
* Base Project: DXVK (Original by doitsujin) v2.7.1
* License: Distributed under the zlib/libpng license.

> NOTE FOR DEVELOPERS: This repository currently hosts compiled binaries and configuration documentation. Source code patches (dxvk_context.cpp and dxvk_context.h) are scheduled for release following the initial public testing phase. 
