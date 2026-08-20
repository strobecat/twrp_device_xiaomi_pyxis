# android_device_xiaomi_vela
For building TWRP for MI CC 9 Meitu Edition

TWRP device tree for MI CC 9 Meitu Edition

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (opengapps, roms, images and so on)
- Backup/Restore (Needs more testing)
- USB OTG

TO-DO:

- Vibration support

## Compile

First checkout minimal twrp with AOSP tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/vela" name="strobecat/twrp_device_xiaomi_vela" remote="github" revision="android-12.1" />
```

Finally execute these:

```
. build/envsetup.sh
lunch twrp_vela-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/vela/recovery.img
```

## Other Sources

Using precompiled stock kernel.

## Thanks

- Thanks to @PeterCxy for the commits and the base: https://github.com/PeterCxy/android_device_xiaomi_violet-twrp
