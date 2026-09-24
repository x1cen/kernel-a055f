# Samsung Galaxy A05 (A055F/M) - Kernel 6.6 Source

Android 15 (One UI 7) custom kernel source for **Samsung Galaxy A05** (`SM-A055F` / `SM-A055M`, MediaTek Helio G85 `MT6768`).

## Features
- **Droidspaces & Linux Containers:** Full support for `NAMESPACES`, `PID_NS`, `IPC_NS`, `USER_NS`, `NET_NS`, `OVERLAY_FS`, `VETH`, `BRIDGE`, `DEVTMPFS`, and `POSIX_MQUEUE`.
- **kABI Compatibility Patch:** Applied padding patch in `include/linux/sched.h` (`ANDROID_KABI_RESERVE`) ensuring MediaTek proprietary vendor modules (`vendor_dlkm`) stay compatible without bootloop.
- **KernelSU:** Embedded KernelSU root support.
- **Automated CI/CD:** GitHub Actions workflow included for automated cloud building.

## Building via GitHub Actions
Go to **Actions** tab in this repository, select **Build Kernel for Samsung Galaxy A05**, and click **Run workflow**. The resulting flashable AnyKernel3 zip will be available in the workflow artifacts.

## Building Locally
### Requirements
- Linux machine (Ubuntu 22.04+ or Debian 12+)
- Build dependencies:
  ```bash
  sudo apt update && sudo apt install -y \
      git build-essential bc bison flex libssl-dev libncurses5-dev \
      libelf-dev python3 python-is-python3 zip unzip curl rsync cpio
  ```

### Build Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/x1cen/kernel-a055f.git
   cd kernel-a055f
   ```
2. Download the Samsung Clang 18 toolchain and extract it into the root of this repo:
   ```bash
   tar -xf toolchain.tar.gz
   ```
3. Run the build script:
   ```bash
   bash build_kernel.sh
   ```
The output AnyKernel3 flashable zip (`a05m-6.6-kernel-*.zip`) will be generated in the root directory.

## Installation
Flash the generated zip using a custom recovery such as **TWRP**.
