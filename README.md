## **[Читать на русском](README-RU.md)**
# lockdownd with PC sync

The patched lockdownd to bypass activation on iOS 4 to 6 while maintaining PC sync functionality.

## Important

This repository contains only the necessary lockdownd file. The full guide is provided below.

The reason I made this repo - [this](https://github.com/iPh0ne4s/iOS-5-6-Hacktivation) lockdownd wasn't working very well with 3utools and at all with iTunes or Finder.

These lockdownds were made by [sn0wbreeze](https://github.com/iH8sn0w/sn0wbreeze/):\
For iOS 6 - iPhone3,2 6.1.3 ipsw, taken from ipsw/048-2727-005.dmg/private/var/stash/lockdownd\
For iOS 5 - iPhone3,3 5.1.1 ipsw, taken from ipsw/038-4297-008.dmg/private/var/stash/lockdownd\
For iOS 4 - iPhone3,1 4.3.3 ipsw, taken from ipsw/038-1423-003.dmg/private/var/stash/lockdownd\
For iOS 3 - iPad 1st gen, 3.? ipsw, taken from ipsw/?/private/var/stash/libexec by [cpalmagu](https://github.com/LukeZGD/Legacy-iOS-Kit/issues/1176)

## Working on
- iPad 2 (all revisions) all 6.x
- iPhone 4S 5.0-6.1.3
- iPod Touch 5 6.0-6.1.3
- iPhone 4 Rev A 6.0-6.1.3
- iPhone 5 6.0-6.1.4
- I hope will work on more devices, but I need testers, test and create an issue so I can expand this list
- I haven't personally tested the iOS 3-5 files, but I'm confident they will work perfectly on devices running the specific firmware versions they were taken from (like iPhone 4 CDMA 5.1.1 and iPhone 4 GSM 4.3.3)

## What this file does

- Bypasses activation on devices running iOS 3 to 6
- Preserves Finder and iTunes synchronization (syncs music unlike iPh0ne4s's file)
- Allows using the device without unlocking with Apple ID or using valid SIM

## Repository contents

- lockdownd - the main file required for the 6.x bypass
- lockdownd-5 - the main file required for the 5.x bypass
- lockdownd-4 - you guessed it, the main file required for the 4.x bypass
- lockdownd-3point2 - do I really need to explain?

# Installation Guide
### If you don't want/don't know how to replace the file, you can use the [Phoenix Ramdisk](https://t.me/phoenixactivator) utility, works on unjailbroken (ramdisk) and jailbroken (OpenSSH) iDevices, at this moment it doesn't work on iOS lower than 4.0

Prerequisites:
- A device running iOS 3 to 6
- Legacy iOS Kit

Step-by-step instructions:

1. Restore the device with jailbreak\
   Use Legacy iOS Kit to restore your device with a jailbreak enabled.

2. Connect via SSH and SFTP\
   Use Legacy iOS Kit to connect via SSH connection to your device. For SFTP use specialized programs (e.g. MobaXterm, FileZilla, etc.).

3. Complete the setup until you reach the iCloud sign‑in screen

4. Replace the lockdownd file\
   Navigate to the following path on your device:
```
/usr/libexec/lockdownd
```
   Replace the existing file with the lockdownd file from this repository.\
   If you're using lockdownd-4 or lockdownd-5, rename it to just "lockdownd" before copying.\
   **Important:** Make sure you downloaded the file for your iOS version, and **ALWAYS backup the original file!**

5. You DON'T need to remove/move Setup.app\
   The setup process goes as normal after file change

6. Set proper permissions (very important, or else you'll get bootloop!)\
   Run the following command via SSH:

```
chmod 755 /usr/libexec/lockdownd
```
   
   OR you can set permissions with SFTP program
   
7. Apply changes\
   Either run:
   
```
ldrestart
```
   
   OR simply reboot your device.

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

- [Automated script](https://t.me/phoenixactivator) ✅
- Test more devices idk

## Disclaimer

Use this at your own risk. The author is not responsible for any damage to your device.

## Credits

- [cpalmagu](https://github.com/LukeZGD/Legacy-iOS-Kit/issues/1176) for iOS 3 file (if you don't like me taking your file DM me in telegram at vacsup i'll remove it)
- [Sn0wbreeze](https://github.com/iH8sn0w/sn0wbreeze/) and its developers for the original method
- [iOS 5-6 Hacktivation](https://github.com/iPh0ne4s/iOS-5-6-Hacktivation) for my first bypass and giving me the idea to fix pc sync
- DeepSeek for helping with README bc i don't know markdown lol
