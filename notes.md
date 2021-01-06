# Various notes on porting

# wlan

* Sometimes indicator-network starts too early and doesn't detect wlan properly leading to wifi menus not appearing in settings

The issue with wlan not loading properly (as well as everything else) was firmware parts not being mounted... See [this commit](https://gitlab.com/ubports/community-ports/android9/oneplus-6/oneplus-enchilada-fajita/-/commit/544919b5c02aa6d36ff63cd61ff3d3f3a8e3d2cb).

# Haptics

* Maybe need [hfd-service.override?](https://github.com/erfanoabdi/rootfs-builder-debos-android9/blob/android9/android9/overlay/etc/init/hfd-service.override)

# SIM card stuff

* Support for [both SIM slots](https://github.com/erfanoabdi/rootfs-builder-debos-android9/commit/9624599beb88a8f7511dd3173175ae04c32151c0)
* [This patch](https://github.com/erfanoabdi/rootfs-builder-debos-android9/commit/715fb34835d3d3676a977ce5ce854c514033670f) might help with mobile data.

## Brightness

* Need [patched repowerd](https://github.com/erfanoabdi/repowerd/commit/afbd490578a252e844b5e8e96b86c325e90b20a9) to use sysfs instead of HAL for brightness control as HAL is broken on op6.

## Resizing system image
```bash
simg2img system.img system.img.raw
resize2fs -f system.img.raw 732160
e2fsck -fy system.img.raw
img2simg system.img.raw system.img.small
```
