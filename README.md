Device configuration for Sony Xperia XZ1 dual sim variant (poplar_dsds)
========================================================

Description
-----------

This repository is for LineageOS 22.1 on Sony Xperia XZ1 dual sim variant (poplar_dsds).

How to build LineageOS
----------------------

* Make a workspace:

        mkdir -p ~/lineageos
        cd ~/lineageos

* Initialize the repo:

        repo init -u git://github.com/LineageOS/android.git -b lineage-22.1

* Create a local manifest:

        cd .repo/
        mkdir local_manifests
        cd ../
        nano .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- Device trees -->
            <project name="Arman-ATI/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="lineage-22.1" />
            <project name="Arman-ATI/android_device_sony_poplar_dsds" path="device/sony/poplar" remote="github" revision="lineage-22.1" />

            <!-- Kernel -->
            <project name="Arman-ATI/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-22.1" />

            <!-- vendor blobs -->
            <project name="Arman-ATI/android_vendor_sony_yoshino-common" path="vendor/sony/yoshino-common" remote="github" revision="lineage-22.1" />
            <project name="whatawurst/android_vendor_sony_poplar_dsds" path="vendor/sony/poplar" remote="github" revision="lineage-21" />
            <project name="Arman-ATI/android_vendor_sony_camera" path="vendor/sony/camera" remote="github" revision="lineage-22.1" />

* Sync the repo:

        repo sync -c --no-clone-bundle --optimized-fetch --prune --force-sync -j$(nproc --all)

* Setup the environment

        source build/envsetup.sh

* Build LineageOS

        brunch poplar_dsds user
