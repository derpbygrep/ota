# Flashing Guide

**WARNING**  
I am not responsible for **bricked devices, lost jobs, dead integrity, or wars.**  
Proceed entirely at your own risk.  

---

## Steps

1. **Unlock the bootloader**  
   Make sure your bootloader is unlocked before proceeding.

2. **Download the required folder** and open a terminal in the directory where it has all downloaded files.

3. **Flash images via Fastboot:**
   ```bash
   fastboot flash init_boot init_boot.img
   fastboot flash boot boot.img
   fastboot flash vendor_boot vendor_boot.img
   fastboot flash recovery recovery.img
   fastboot -w
   fastboot reboot recovery
   ```

4. **While in recovery mode, format data.**

5. **Sideload the ROM**  
   From recovery, use:
   ```bash
   adb sideload <filename>.zip
   ```

---

## Sideload Error

- **Error 7 during sideload**  
  If sideload fails with *error 7*:
  1. Reboot into **fastbootd** (from recovery → enter fastboot option).  
  2. Wipe the super partition:  
     ```bash
     fastboot wipe-super super_empty.img
     ```
  3. Return to recovery and sideload again.
