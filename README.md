# Lord Kernel

A customized android kernel for SM8350 SoC

<img width="300" alt="Screenshot_20251115-193653_NetHunter Terminal" src="https://github.com/user-attachments/assets/0bd84eea-ee69-45df-af0a-d36b8569ec37" />
<img width="300" alt="Screenshot_20251115-193733_Settings" src="https://github.com/user-attachments/assets/a3a6aa11-f0cc-43b9-90d7-538d0edd2c12" />

### TP-link AC600 (rtl8821au) adapter working
<img width="500"  alt="lord-dev-testing-low-res" src="https://github.com/user-attachments/assets/3166cbb5-3677-40ce-ba70-3f115f5071bf" />

</br>

Based on https://github.com/Spanish-or-Vanish/kernel_xiaomi_sm8350

Devices supported: Xiaomi 11t Pro (vili)

Development branch: lord-dev @ https://github.com/loystonpais/android_kernel_qcom_sm8350/tree/lord-dev

# What's New (v0.0.8+)

The built-in wlan now supports frame injection. 

Props to this dude for figuring it out: https://medium.com/h7w/they-said-packet-injection-on-qcacld-3-0-was-impossible-i-proved-them-wrong-588fa55ee702

To easily toggle between monitor and managed mode you can use this script:
```sh
set -e

case "$1" in
  monitor)
    ip link set wlan0 down
    echo 4 | sudo tee /sys/module/wlan/parameters/con_mode > /dev/null
    ip link set wlan0 up
    echo "Monitor mode enabled"
    ;;
  managed)
    ip link set wlan0 down
    echo 0 | sudo tee /sys/module/wlan/parameters/con_mode > /dev/null
    ip link set wlan0 up
    echo "Managed mode enabled"
    ;;
  toggle)
    mode=$(cat /sys/module/wlan/parameters/con_mode)
    if [ "$mode" = "4" ]; then
      $0 managed
    else
      $0 monitor
    fi
    ;;
  status)
    mode=$(cat /sys/module/wlan/parameters/con_mode)
    case "$mode" in
      0) echo "managed" ;;
      4) echo "monitor" ;;
      *) echo "($mode)" ;;
    esac
    ;;
  *)
    echo "Usage: wlan0 [monitor|managed|toggle|status]" >&2
    exit 1
    ;;
esac
```


# Features

1. KernelSU Next for root
1. Nethunter Patches
1. Qcacld 3.0 Injection Patches 
1. External WiFi adapter support (rtw88) (ex: RTL8821AU) 
1. Support for running docker container and Droidspaces
1. Btrfs, ntfs and exfat are supported

# Warning ⚠️

This kernel is for advanced users.

# Usage

To use the kernel simply flash the anykernel zip via TWRP or any custom recovery.

For rtw88 support, flash rtw88 firmware magisk module from the link given below.

For nethunter, flash the nethunter module from the link given below.

If things do not work as expected, open an issue.

Some tips below: 

> Before flashing, backup boot, vendor_boot, dtbo & super. You can restore them back later to return to the original state

> Flash latest firmware

> Disable HIDE SUS MOUNTS FOR ALL PROCESSES if you are using susfs (fixes issues with chroot mounting)

# Related

https://github.com/kimocoder/qualcomm_android_monitor_mode - Enabling monitor mode for built-in wlan

https://github.com/ravindu644/Droidspaces-OSS - Droidspaces

https://github.com/loystonpais/rtw88/releases - RTW88 Firmware magisk module

https://github.com/SherlockChiang/Nethunter_for_KernelSU - Nethunter module for kernelsu. It's recommended that you update the rootfs.

https://github.com/sidex15/susfs4ksu-module/issues/86 - Alternative fix for nethunter chroot mount issues with susfs. Basically you need to run `su -c ksu_susfs hide_sus_mnts_for_all_procs 0` before mounting.

