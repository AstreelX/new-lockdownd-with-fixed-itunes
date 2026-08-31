## **[Читать на русском](README-RU.md)**
# lockdownd with PC sync

The patched lockdownd to bypass activation on iOS 3 to 6 while maintaining PC sync functionality.

## Important

This repository contains only the necessary lockdownd files. The full guide is provided below.

The reason I made this repo - [this](https://github.com/iPh0ne4s/iOS-5-6-Hacktivation) lockdownd wasn't working very well with 3utools and at all with iTunes or Finder.

These lockdownds were made by [sn0wbreeze](https://github.com/iH8sn0w/sn0wbreeze/):\
For iOS 6 - iPhone3,2 6.1.3 ipsw, taken from ipsw/048-2727-005.dmg/private/var/stash/lockdownd\
For iOS 5 - iPhone3,3 5.1.1 ipsw, taken from ipsw/038-4297-008.dmg/private/var/stash/lockdownd\
For iOS 4 - iPhone3,1 4.3.3 ipsw, taken from ipsw/038-1423-003.dmg/private/var/stash/lockdownd

For iOS 3 - iPad 1st gen, 3.? ipsw, taken from ipsw/?/private/var/stash/libexec/lockdownd **personally by [cpalmagu](https://github.com/LukeZGD/Legacy-iOS-Kit/issues/1176)**

## 📱 Compatibility Matrix
### **Legend:**
* ✅ = Fully Working
* ⏳ = Planned for testing, but should work
* ❌ = iOS version not supported by hardware
### ⚙️ Apple A4 - A6(X) Devices

| Device Model | Chip | iOS 4.x | iOS 5.x | iOS 6.x | Status & Notes |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **iPhone 4 (GSM)** `iPhone3,1` | A4 | ✅ | ✅ | ✅ | Every version works |
| **iPhone 4 (CDMA)** `iPhone3,3` | A4 | ⏳ | ✅ | ⏳ | Every version should work |
| **iPod Touch (4th Gen)** `iPod4,1` | A4 | ✅ | ✅ | ✅ | Every version works |
| **iPhone 4S** `iPhone4,1` | A5 | ❌ | ✅ | ✅ | Every version works |
| **iPad (2nd gen)** `iPad2,1-2,3` | A5 | ⏳ | ⏳ | ✅ | Every version should work |
| **iPad (3rd Gen)** `iPad3,1-3,3` | A5X | ❌ | ⏳ | ⏳ | Planned for testing |
| **iPad Mini (1st Gen)** `iPad2,5-2,7`| A5 | ❌ | ❌ | ⏳ | Planned for testing |
| **iPod Touch (5th Gen)** `iPod5,1` | A5 | ❌ | ❌ | ✅ | Every version works |
| **iPhone 5** `iPhone5,1` / `iPhone5,2` | A6 | ❌ | ❌ | ✅ | Every version works |
| **iPad (4th Gen)** `iPad3,4-3,6` | A6X | ❌ | ❌ | ⏳ | Planned for testing |

### 📜 Legacy & Rev A Devices

| Device Model | Chip | iOS 3.x | iOS 4.x | iOS 5.x | iOS 6.x | Status & Notes |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **iPod Touch (3rd Gen)** `iPod3,1` | Samsung S5L8922 | ⏳ | ⏳ | ⏳ | ❌ | Planned for testing |
| **iPad (1st Gen)** `iPad1,1` | A4 | ✅ | ⏳ | ⏳ | ❌ | 3.x works, others are planned for testing |
| **iPhone 4 (Rev A)** `iPhone3,2` | A4 | ❌ | ❌ | ❌ | ✅ | Every version works |
| **iPad 2 (Rev A)** `iPad2,4` | A5 | ❌ | ❌ | ❌| ✅ | Every version works |

## What this file does

- Bypasses activation on devices running iOS 3 to 6
- Preserves Finder and iTunes synchronization (syncs music unlike iPh0ne4s's file)
- Allows using the device without unlocking with Apple ID or using valid SIM

## Repository contents
All files are in a folder called "lockdownd's"
- lockdownd-6 - the main file required for the 6.x bypass
- lockdownd-5 - the main file required for the 5.x bypass
- lockdownd-4 - you guessed it, the main file required for the 4.x bypass
- lockdownd-3 - do I really need to explain?

# Installation Guide
### If you don't want/don't know/don't want to know how to replace the file, you can use the [Phoenix Ramdisk](https://t.me/phoenixactivator) utility, works on unjailbroken (ramdisk) and jailbroken (OpenSSH) iDevices, currently supports iOS 4.0 and above only, also available in Releases tab

## Prerequisites:
- A device running iOS 3 to 6
- Legacy iOS Kit
- SSH or/and SFTP client
- Patience, a lot of it

## Step-by-step instructions:

1. Restore the device with jailbreak\
   Use Legacy iOS Kit to restore your device with a jailbreak enabled.

2. Connect via SSH and SFTP\
   Use Legacy iOS Kit to connect via SSH connection to your device. For SFTP use specialized programs (e.g. MobaXterm, FileZilla, etc.).

3. Complete the setup until you reach the iCloud sign‑in screen (or another error that prevents further setup like "Unknown device" or SIM requirement)

4. Replace the lockdownd file\
   Navigate to the following path on your device:
```
/usr/libexec/lockdownd
```
   Replace the existing file with the lockdownd file from this repository, rename it to just "lockdownd" before copying.
   
### **Important:** Make sure you downloaded the file for your iOS version, and **ALWAYS backup the original file by renaming or downloading it!**
### **VERY Important:** iOS 3.x replacing process is different from 4-6, the path is not /usr/libexec but /private/var/stash/libexec
   
5. You DON'T need to remove/move/rename Setup.app\
   The setup process goes as normal after file change

6. Set proper permissions (very important, or else you'll get bootloop!)\
   Run the following command via SSH:

```
chmod 755 /usr/libexec/lockdownd
```
   
   OR you can set permissions with SFTP program.
   
7. Apply changes\
   Either run  `ldrestart` OR simply reboot your device.

## For CoolBooter users

If you're using a coolbooter partition, you can't use SFTP while on the activation screen (OpenSSH is not preinstalled, I suppose? Didn't work for me anyway). Instead:

1. Boot an SSH ramdisk using Legacy iOS Kit (A5(X) users will need checkm8-a5 or kDFUApp)
2. Mount the coolbooter partition manually:
```
mount_hfs /dev/disk0s1s3 /mnt1
```
(instead of using `mount.sh`)
3. Replace the lockdownd file as described above
4. Reboot and complete the setup

## After installation

Your device should now have activation bypassed while retaining the ability to sync with your PC via USB cable.

## Todo list

- [Automated tool](https://t.me/phoenixactivator) ✅
- Test more devices (help me with it)

## Disclaimer

Use this at your own risk. The author is not responsible for any damage to your device.

## Credits

- [cpalmagu](https://github.com/LukeZGD/Legacy-iOS-Kit/issues/1176) for iOS 3 file, legend
- [Sn0wbreeze](https://github.com/iH8sn0w/sn0wbreeze/) and its developers for the original method
- [iOS 5-6 Hacktivation](https://github.com/iPh0ne4s/iOS-5-6-Hacktivation) for my first bypass and giving me the idea to fix pc sync
- DeepSeek for helping with README bc i don't know markdown lol
