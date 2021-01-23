Device Checklist
================

This Checklist is a supplement for all porters to be able to inform users in detail about their progress, as well as track their readiness for being added as a community or core device.

For either qualifying as a community or a core device a corresponding feature set from the list below needs to be confirmed working. The details will be published soon here.

For the convenience of your users present this list in the following way:

Working
-------

* Actors: Notification LED
* Misc: Anbox patches applied to kernel
* GPU: Boot into UI
* Camera: Flashlight
* Camera: Photo
* Camera: Video
* Camera: Switch between back and front camera
* Bluetooth: Driver loaded at startup
* Bluetooth: Enable/disable and flightmode works
* Bluetooth: Persistent MAC address between reboots
* Bluetooth: Pairing with headset works, volume control ok
* Cellular: Carrier info, signal strength
* Cellular: Data connection
* Cellular: Enable/disable mobile data and flightmode works
* Misc: AppArmor patches applied to kernel
* Misc: Battery percentage
* Misc: Offline charging (Power down, connect USB cable, device should not boot to UT)
* Misc: Online charging (Green charging symbol, percentage increase in stats etc)
* WiFi: Persistent MAC address between reboots
* WiFi: Driver loaded at startup
* WiFi: Enable/disable and flightmode works
* Sensors: Rotation
* Sensors: Touchscreen
* Sound: Earphones detected, volume control
* Sound: Loudspeaker
* Sound: Microphone
* Misc: Shutdown / Reboot
* Sound: Loudspeaker volume control


Working with additional steps
-----------------------------

* Actors: Torchlight - need https://github.com/ubports/indicator-power/commit/a5d15893826c8e9e9e86b26911fc26ecc912ea3f which isn't in stable yet, deb available here: https://ci.ubports.com/job/ubports/job/indicator-power/job/xenial_-_android9/3/artifact/indicator-power_12.10.8+ubports2+0~20210122175117.3~1.gbp9966c9_arm64.deb just install and reboot

* Actors: Vibration - waiting for https://github.com/ubports/hfd-service/pull/13 to be merged, can install https://ci.ubports.com/job/hfd-service/job/PR-13/4/artifact/hfd-service_0.1.0+0%7E20210121155028.4%7E1.gbp6bc0ac_arm64.deb

* Actors: Manual brightness - need erfan repowerd fork
* Sensors: Automatic brightness - same as above

Not working
-----------

Put all working features in under the first headline. Put features where the user needs to to additonal (manual) steps under the second headline. Everything else goes under the third headline.

Untested
--------

* Cellular: Incoming, outgoing calls
* Cellular: MMS in, out
* Cellular: PIN unlock
* Cellular: SMS in, out
* Cellular: Change audio routings
* Cellular: Voice in calls
* Cellular: Switch connection speed between 2G/3G/4G works for all SIMs
* Cellular: Switch preferred SIM for calling and SMS - only for devices that support it
1234

* Endurance: Battery lifetime > 24h from 100%
* Endurance: No reboot needed for 1 week

* GPU: Hardware video decoding


* Misc: Recovery image builds and works
* Misc: Reset to factory defaults
* Misc: Date and time are correct after reboot (go to flight mode before)

* (Network: NFC - disabled atm due to no middleware)


* WiFi: Hotspot can be configured, switched on and off, can serve data to clients

* Sensors: Fingerprint reader, register and use fingerprints (Halium 9.0 only)
* Sensors: GPS
* Sensors: Proximity

* USB: MTP access
* (USB: ADB access - disabled atm due to no middleware)
* USB: External monitor - only for devices that support it
