# Lord Kernel

<img width="300" alt="Screenshot_20251115-193653_NetHunter Terminal" src="https://github.com/user-attachments/assets/0bd84eea-ee69-45df-af0a-d36b8569ec37" />
<img width="300" alt="Screenshot_20251115-193701_KernelSU Next" src="https://github.com/user-attachments/assets/499a1111-359a-42d0-8d1e-ac146f460fb8" />
<img width="300" alt="Screenshot_20251115-193733_Settings" src="https://github.com/user-attachments/assets/a3a6aa11-f0cc-43b9-90d7-538d0edd2c12" />


Based on https://github.com/Spanish-or-Vanish/kernel_xiaomi_sm8350

Devices supported: Xiaomi 11t Pro (vili)

Development branch: lord-dev @ https://github.com/loystonpais/android_kernel_qcom_sm8350/tree/lord-dev

# Features

1. KernelSU Next + susfs
1. Nethunter Patches
1. Several kernel features enabled to support docker
1. Btrfs, ntfs and exfat are supported


# Warning ⚠️

This kernel is for advanced users.

# Notes

1. Flash the anykernel zip via TWRP
1. Before flashing, please backup boot, vendor_boot, dtbo & super. You can restore them back later to return to the original state
2. Things not working? Make a github issue or use the discussions feature

# Related

https://github.com/SherlockChiang/Nethunter_for_KernelSU - Nethunter module for kernelsu. It's recommended that you update the rootfs.

https://github.com/sidex15/susfs4ksu-module/issues/86 - Fix for nethunter chroot mount issues. You need to run `su -c ksu_susfs hide_sus_mnts_for_all_procs 0` before mounting.
