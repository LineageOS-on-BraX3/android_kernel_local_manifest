BraX3 kernel building
===========

Getting started
---------------

To get started with Android, you'll need to get familiar with [Source Control Tools](https://source.android.com/setup/develop).

To initialize your local repository using the Google kernel manifest, use a command like this:
```
repo init -u https://android.googlesource.com/kernel/manifest.git -b common-android13-5.15
```
Then to sync up:
```
repo sync
```

Building the kernel (legacy)
-------------------
To build the GKI kernel image and the device kernel modules, use a command like this at the root of your local repository:
```
build/build.sh
```
Then every built artifacts are available at:
```
out/android13-5.15/dist
```

Updating the prebuilt kernel repository
---------------------------------------
To succesfully updat the [prebuilt kernel repository](https://github.com/LineageOS-on-BraX3/android_device_brax_X3-kernel.git), use a command like this at the root of your local repository:
```
cp out/android13-5.15/dist/Image.lz4 path/to/prebuilt/kernel/repository
cp out/android13-5.15/dist/kernel-uapi-headers.tar.gz path/to/prebuilt/kernel/repository
cp out/android13-5.15/dist/dtbo.img path/to/prebuilt/kernel/repository
cp out/android13-5.15/dist/mt6835.dtb path/to/prebuilt/kernel/repository/dtb
rsync -av --files-from=kernel-brax/X3-modules.txt out/android13-5.15/dist path/to/prebuilt/kernel/repository/modules
```
