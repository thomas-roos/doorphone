# Build Process Guidelines for AmebaProII Doorbell

## Prerequisites
- ARM GCC toolchain installed from ARM developer site
- Setup script already run from parent directory
- Git with submodule support
- CMake build system

## Build Sequence (from this directory)
1. **Submodule Init**: `git submodule update --init --recursive`
2. **Navigate**: `cd project/realtek_amebapro2_webrtc_application/GCC-RELEASE`
3. **Build Setup**: `mkdir build && cd build`
4. **Configure**: `cmake .. -G"Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=../toolchain.cmake`
5. **Build & Flash**: `cmake --build . --target flash -j$(nproc)`

## Build Troubleshooting
- Verify ARM GCC toolchain in PATH
- Check submodule initialization if build fails
- Ensure toolchain.cmake exists and is correct
- Verify hardware connection for flashing

## File Dependencies
- `doorbell_config.h` (should exist from setup script)
- `doorbell_master.c` (should exist from setup script)
- Modified `master.c` (should be updated from setup script)

## Build Targets
- Default: `cmake --build . -j$(nproc)`
- `flash`: `cmake --build . --target flash -j$(nproc)`
- Clean builds recommended after config changes
