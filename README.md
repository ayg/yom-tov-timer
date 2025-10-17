# Yom Tov Timer
Automatically turn devices on and off for Shabbos and yom tov

## Summary

This code allows turning devices on and off on a timer that knows when Shabbos and yom tov are. Unlike a standard digital timer, it will automatically account for yom tov and for changes in sunset time, to give you fewer things to think about erev Shabbos/yom tov. It can disable light switches so that pushing them will not toggle the light. For each thing you want to control, you will need to purchase an appropriate [Shelly](https://www.shelly.com/) device, which should cost around $15-25. Setup currently requires some technical know-how but should only take a few minutes. If you're trying to control something like a light fixture that's hardwired (not an outlet), a bit of electrical wiring will probably be needed.

## Setup instructions

1. Choose and obtain an appropriate Shelly device (see [Which device](#which-device)). Shelly has online stores in the [USA](https://us.shelly.com/), [EU](https://www.shelly.com/), and [UK](https://shellystore.co.uk/), and Shelly devices can be purchased from many other outlets as well. For Israel, the best bet is probably [the Shelly AliExpress store](https://shelly.aliexpress.com/store/), which offers free shipping to Israel.
2. When the device is powered on and there is a Wi-Fi network available for it to connect to, go next to it with a computer with Wi-Fi and connect the computer to a Wi-Fi network called something starting with "Shelly", like "Shelly1PMMiniG3-2E4A4782FEA1".
3. Navigate in a web browser to [http://192.168.33.1/](http://192.168.33.1/#/).
4. Click "Configure Wi-Fi Settings" and provide the requested information. Check "Enable", pick your network from the drop-down, enter the password, and click "Save settings". "Wi-Fi status" at the top should now say the name of the network, an IP address, and a connection strength rating (RSSI).
X. [do this at the end, duh] Go to [http://192.168.33.1/#/settings/access-point](http://192.168.33.1/#/settings/access-point) (icon at the top right with tooltip "AP enabled") and disable the access point, so that others will not be able to take over your device remotely.


2. Go to [Shelly Cloud](https://control.shelly.cloud/) and log in.
3. Click Add Device toward the bottom left.
4. Select Include Device via Web Bluetooth.
5. Click Next, wait for a dropdown to show up in your browser, select the device from the drop-down, and click Pair.
6. Set up the Wi-Fi info and click Next. Disable access point and Bluetooth.
7. Pick and name, and if you want set a room, then click Save.
8. Click on your new device, and in the side panel at the right, click on the single gear icon at the left all the way at the bottom to open settings (not the double gear icon two above it).
9. Click "Firmware version" and click "Update". When prompted, click "Update firmware" to confirm.
10. When the device becomes available again, click the "{ }" icon to open the Scripts tab. Click "Create new script". Enter a name like "setup_schedules", and paste the code from shelly.js in this repository there. Go to the place where it says "EDIT" and uncomment something that is suitable for you, adjusting as appropriate. Click the "Save" icon in the upper right, and once it's saved, click the "Run" icon. You should receive a green "The script has been started!" notification.
11. Click the X in the upper right, and go to the schedule tab (calendar icon). The first schedule should run every day in the middle of the night and say "{ } Script.start". The others should reflect what you want the device to do and when. Look at them carefully to make sure they do what you intend.
12. Go back to the settings tab, "Input/output settings", and set "Set relay power on default" to "Configure Shelly device to Restore the last mode it was in, when it has power."
13. It's advisable check that "Geo location and time zone" is set correctly, to make sure that sunset times and DST will be handled correctly.

## Which device?

For appliances that plug in to outlets, the easiest option is a Shelly Plug of some kind. Make sure the plug type matches your country. If you're using it for something that uses a lot of power, like an oven or air conditioner, check that your device is within the maximum power rating for the plug. Shelly doesn't have smart plugs for Israeli outlets, but you could use two plug adapters, one on each side. (If using plug adapters, it's probably best to plug it into a short extension cord and not horizontally into a wall -- the torque of four plugs in a row might be too much for the plug to stay firmly in the wall.)

For lights, you could use a Shelly Bulb (make sure the socket type is correct), but this will not let you turn the light on when the switch is off. This might be a good solution if you just want to make sure the light is always off on Shabbos, e.g., for a bedroom.
