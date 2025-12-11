# Doorbell Master - AmebaProII

Alternative master implementation for Realtek AmebaProII using FreeRTOS WebRTC.

## Automated Setup

### 1. Run Setup Script
```bash
cd ..
./setup-aws-and-config.sh
```

The script automatically:
- Generates `doorbell_config.h` with your AWS settings
- Copies files to FreeRTOS project
- Modifies `master.c` to include doorbell task

### 2. Build and Flash
```bash
cd master-amebapro/freertos-webrtc-amebapro

# Initialize submodules
git submodule update --init --recursive

# Navigate to project
cd project/realtek_amebapro2_webrtc_application/GCC-RELEASE

# Create build directory
mkdir build
cd build

# Generate Makefile
cmake .. -G"Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=../toolchain.cmake

# Build and flash
cmake --build . --target flash
```

**Note:** You need ARM GCC toolchain installed. Download from:
https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads

Done! Your AmebaProII is now a video doorbell.

## What the Script Does

1. Creates `doorbell_config.h` with:
   - AWS IoT endpoint
   - KVS channel name
   - AWS credentials
   - MQTT topic (auto-generated)

2. Copies to FreeRTOS project:
   - `doorbell_config.h`
   - `doorbell_master.c`

3. Modifies `master.c`:
   - Adds `#include "doorbell_master.c"`
   - Adds `xTaskCreate(doorbellMasterTask, ...)`

## Hardware

- Built-in Program Button (PB_31) used as doorbell trigger
- Camera module (from FreeRTOS WebRTC reference)

## How It Works

Button press → MQTT notification → Viewer connects → WebRTC video stream
