### Port status

|         Component | Status | Details            |
|------------------:|:------:|--------------------|
|          AppArmor |    Y   |Some webapps seems to crash, but this is not device specific issue |
|      Boot into UI |    Y   |Sometimes it boots, and after some time (not longer than 2 minutes from boot screen turns black, reboot fix everything. SSH seems to work. |
|            Camera |    Y   | If app crashes after taking photo try switching cameras and turning flash on, and off. Black screen on app - reboot. |
|    Cellular Calls |    Y   | They work. But not always you are able to take call, make a call or end it. App seems to hang, and I didn't found anything useful in logs. |
|     Cellular Data |    Y   | Have problems with adding custom APN |
|               GPS |    Y   |                    |
|           Sensors |    Y   | Screen orientation works, but some apps do not see anything when I rotate my phone (there was a game about it..) |
|             Sound |    Y   | Sometimes when you have headphones connected and receive notification audio starts to play on phone's speakers... |
| UBPorts Installer |    N   |                    |
|  UBPorts Recovery |    N   |                    |
|          Vibrator |    Y   | When (mis)used veeeery frequently it stops working untill reboot. |
|             Wi-Fi |    Y   | Sometimes (not often) you get disconnected |

### TODO

 - [ ] Make device specific system.img
 - [ ] Make UBPorts Installer working
 - [ ] Fix calls
