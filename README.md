# How to install ubuntu touch
* Flash OOS 9 from twrp, go to reboot menu and select again the same slot as the one listed as active, reboot to bootloader and boot into twrp again, go to the reboot menu and make sure it is the same slot as before, if not then select it and repeat. Then flash lineage 16
* Reboot again into twrp, you should now be on the other slot. Flash GSI v9
* Reboot into bootloader and run `fastboot flash boot halium-boot.img` - get halium boot from here: https://build.lolinet.com/file/halium/enchilada/ or https://build.lolinet.com/file/halium/fajita/
* Boot twrp again and flash halium ramdisk from here: https://build.lolinet.com/file/halium/GSI/tools/halium-ramdisk.zip

# Issues

If you get stuck on the boot animation screen, run `ssh phablet@10.15.19.82` from your host (password: `phablet`)
Then run the following:
```
sudo -s
<phablet>
mount -o remount,rw /
cat /var/lib/lxc/android/rootfs/ueventd*.rc /vendor/ueventd*.rc | grep ^/dev | sed -e 's/^\/dev\///' | awk '{printf "ACTION==\"add\", KERNEL==\"%s\", OWNER=\"%s\", GROUP=\"%s\", MODE=\"%s\"\n",$1,$3,$4,$2}' | sed -e 's/\r//' >/etc/udev/rules.d/70-ubport.rules
```