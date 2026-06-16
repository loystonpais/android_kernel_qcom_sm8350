# Lord Kernel

A customized android kernel for SM8350 SoC

<img width="300" alt="Screenshot_20251115-193653_NetHunter Terminal" src="https://github.com/user-attachments/assets/0bd84eea-ee69-45df-af0a-d36b8569ec37" />
<img width="300" alt="Screenshot_20251115-193733_Settings" src="https://github.com/user-attachments/assets/a3a6aa11-f0cc-43b9-90d7-538d0edd2c12" />

### Working of tp-link ac600 (rtl8821au) adapter
<img width="500"  alt="lord-dev-testing-low-res" src="https://github.com/user-attachments/assets/3166cbb5-3677-40ce-ba70-3f115f5071bf" />

</br>

Based on https://github.com/Spanish-or-Vanish/kernel_xiaomi_sm8350

Devices supported: Xiaomi 11t Pro (vili)

Development branch: lord-dev @ https://github.com/loystonpais/android_kernel_qcom_sm8350/tree/lord-dev

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

> Before flashing, please backup boot, vendor_boot, dtbo & super. You can restore them back later to return to the original state

> Flash latest firmware !!!

> Disable HIDE SUS MOUNTS FOR ALL PROCESSES if you are using susfs (fixes issues with chroot mounting)

1. Flash the anykernel zip in releases via TWRP
1. Flash rtw88 firmware magisk module from the given link below
1. Flash nethuter module from link given below
1. Things not working? Make a github issue or use the discussions feature

# Related

https://github.com/kimocoder/qualcomm_android_monitor_mode - Enabling monitor mode for built-in wlan

https://github.com/loystonpais/rtw88/releases - RTW88 Firmware magisk module

https://github.com/SherlockChiang/Nethunter_for_KernelSU - Nethunter module for kernelsu. It's recommended that you update the rootfs.

https://github.com/sidex15/susfs4ksu-module/issues/86 - Alternative fix for nethunter chroot mount issues with susfs. Basically you need to run `su -c ksu_susfs hide_sus_mnts_for_all_procs 0` before mounting.

