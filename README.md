<img width="1152" height="768" alt="STAR-ENGINE-DXVK" src="https://github.com/user-attachments/assets/93a4ce07-1e87-4bf5-a528-e0b99be02c44" />

# 🌟 STAR ENGINE: DXVK v2.7.2.1 (HAAE Update)
[![Sponsor](https://img.shields.io/badge/Sponsor-%24?logo=github&style=flat)](https://github.com/sponsors/isygold)

### **Adaptive High-Performance DXVK Fork for Android Emulation**

**STAR ENGINE** is a specialized performance modification of DXVK designed specifically for **Qualcomm Adreno GPUs** in mobile environments (Star Emulator, Winlator, Mobox). This fork prioritizes **Frame Pacing Stability** and **Driver Survival** over raw, stuttery peak FPS.

---

## 🆕 What's New in v2.7.2.1

### 🤖 Adaptive Command Stream (Auto-Threshold)(Experimental/not yet implented for use yet but will be in v2.7.3)
The engine now features real-time frame telemetry monitoring to balance performance and safety automatically.
* **Dynamic Pacing:** Automatically adjusts the Mid-Frame Flush threshold based on GPU load.
* **Smart Performance:** High-FPS scenes allow larger command batches, while heavy scenes trigger frequent flushes to prevent **Adreno Driver Hangs**.

### 🖼️ Tiered Adaptive Scaling (HAAE Vision)
Implemented a hardware-aware upscaling layer to reclaim performance lost to mobile resolution bottlenecks.
* **Performance Tier:** Uses optimized Linear Blit for low-end GPUs (SD6xx).
* **Quality Tier:** Triggers **Cubic Reconstruction** for high-end GPUs (SD7xx/8xx) when performance headroom exists.
* **Resolution Fix:** Improved handshake between D3D swapchains and Android displays to fix resolution mismatches in legacy titles.

### 🛠️ Unity Engine "Initialization" Fixes
Added core DXVK patches to solve the common **"Failed to initialize 3D engine"** errors.
* **Shader Zero-Init:** Prevents Unity from reading garbage memory, fixing splash-screen crashes.
* **D3D11 Modernization:** Implementation of `ID3DDestructionNotifier` and improved Planar Video paths for modern Unity titles.

---

## 🚀 Key Technical Features
* **Dynamic-State-Aware Bind-Skip:** Reduces CPU overhead by skipping redundant pipeline calls unless dynamic states (viewports/scissors) change.
* **Mid-Frame Command Flushing:** Prevents command buffer overflows—a critical fix for Adreno 610/642L/7xx/8xx GPUs.
* **Android-Native Storage Support:** Intelligent configuration loading from common Android paths for easier setup on mobile devices.

---

## 🛠️ Installation & Setup

### Method 1: Star Emulator (Recommended)
1. Open Star Emulator.
2. Navigate to the **"Contents"** menu.
3. Install the `dxvk-2.7.2.1.wcp` file.

### Method 2: Manual Config (Plug-and-Play)
Place your `dxvk.conf` or `starengine.ini` in any of these supported paths:
* `/storage/emulated/0/Winlator/`
* `/storage/emulated/0/Download/`
* `/storage/emulated/0/`

**Environment Variable Configuration:**
* **Name:** `DXVK_CONFIG_FILE`
* **Value:** The directory where your `dxvk.conf` is located (e.g., `/sdcard/Winlator/dxvk.conf`).

------

## 📝 **Dev/User Note: Why 2.7.2.1 uses Manual Thresholds Internal** 
* **Project Note: Core Branch 2.7.2.1 vs. 2.7.3 Roadmap**

**"The decision to retain manual thresholding in the 2.7.2.1 release was made to ensure absolute stability during the transition to the new HAAE Upscaling Layer. While the Auto-Adaptive logic is mathematically sound, implementing it in the current branch without real-time GPU Load telemetry (utilization %) would lead to 'threshold oscillation' on mid-range devices like the SD680.
We are delaying the AUTO-THRESHOLD SYSTEM to v2.7.3 to allow for a deeper integration with the Mesa/Turnip GPU Statistics framework. This will allow the engine to distinguish between a CPU-bound stutter and a GPU-bound overflow, preventing unnecessary command flushing and preserving maximum FPS."**

------

---

## ⚙️ Configuration Tuning
You can modify your `dxvk.conf` to find the perfect balance for your specific hardware:

```ini
# STAR ENGINE CONFIG
starengine.adaptiveThreshold = 1    # 1 = Auto (Recommended), 0 = Manual(Experimental/yet to be implemented)
starengine.drawThreshold = 150      # Only used if Adaptive is 0
starengine.bindSkip = 1             # Change based on level of game stuttering
starengine.allowQualityScaling = 1  # 1 for High-End (Cubic), 0 for Low-End (Linear)(Experimental/yet to be implemented)
```
------
------

## NOTE (FOR BIONIC VERSION USAGE): 
* The turnip version 25.1.0 as default does not properly communicate with this dxvk driver hence should not be used as it will not work! properly install the latest turnip driver that is good or compatible for your device performance. All installations and manual placing should be done before the creating a container and the drivers are to be set during installation as this ensures a clean setup! 
* Also the box 64 version is to be considered; version 0.3.6/ 0.3.6-xxxx for stability usage with this driver(this can be as a fall back for performance) versions 0.3.7/0.3.7-xxxx - 0.4.xxxx variant are recommended for better performance.( This relies greatly and depends on the Device used)
* The tests in the container will have low fps beacuse of the draw call threshold being set but will notice a very smooth frame pacing and smoother test and smoother gameplay, which is the main aim of the driver, this applies in the game as well depending on your specific hardware device (GPUS with 6xx-7xx and 8s gen 1 too will be working good for this driver). If you're judging the speed based on the built-in container tests or system tools, don't trust them! They don't handle the Async paths in STAR ENGINE properly. Test with an actual game (like Tomb Raider or RE) and turn on the DXVK_HUD to make sure the engine is actually loading.
* You can tweak your dxvk.conf to better suit your specific game having heavy stutter and lags which help in reducing its issue, but remember to always have a copy of your previous tweaked or default dxvk.conf file incase you want to fallback to it.
* Provide log files when placing issues down it helps a lot to pinpoint the exact issues.
* Make sure to avoid mistakes when inputing the environment variables as this is crucial for this versio
* For max performance locking use the FEXCORE and VKD3D+DXVK and DGVOODO
------
------

## 📜 Credits & License
* Lead Developer: ISYGOLD
* Base Project: DXVK (Original by doitsujin) v2.7.1
* License: Distributed under the zlib/libpng license.

> NOTE FOR DEVELOPERS: Follow the Readme instructions in both the build/compilation folder and the source code folder to get successful build.
