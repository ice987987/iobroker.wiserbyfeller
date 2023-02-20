![Logo](admin/wiserbyfeller.svg)

# ioBroker.wiserbyfeller

[![NPM version](https://img.shields.io/npm/v/iobroker.wiserbyfeller.svg)](https://www.npmjs.com/package/iobroker.wiserbyfeller)
[![Downloads](https://img.shields.io/npm/dm/iobroker.wiserbyfeller.svg)](https://www.npmjs.com/package/iobroker.wiserbyfeller)
![Number of Installations](https://iobroker.live/badges/wiserbyfeller-installed.svg)
![Current version in stable repository](https://img.shields.io/badge/stable-not%20published-%23264777)

<!-- ![Current version in stable repository](https://iobroker.live/badges/wiserbyfeller-stable.svg) -->
<!-- [![Dependency Status](https://img.shields.io/david/ice987987/iobroker.wiserbyfeller.svg)](https://david-dm.org/ice987987/iobroker.wiserbyfeller) -->

[![NPM](https://nodei.co/npm/iobroker.wiserbyfeller.png?downloads=true)](https://nodei.co/npm/iobroker.wiserbyfeller/)

![Test and Release](https://github.com/ice987987/ioBroker.wiserbyfeller/workflows/Test%20and%20Release/badge.svg)

[![Donate](https://img.shields.io/badge/donate-paypal-blue?style=flat)](https://paypal.me/ice987987)

## wiserbyfeller adapter for ioBroker

This Adapter enables you to manage all your Wiser-by-Feller system devices via a WebSocket connection.

## Disclaimer

All product and company names or logos are trademarks™ or registered® trademarks of their respective holders. Use of them does not imply any affiliation with or endorsement by them or any associated subsidiaries! This personal project is maintained in spare time and has no business goal. Wiser by Feller is a trademark of Feller AG, CH-8810 Horgen.

## Installation requirements

-   node.js >= v14.0 is required
-   js-controller >= v4.0.23 is required
-   admin >= v6.2.19 is required
-   Installed Wiser by Feller devices are required. More information can be found here: [Wiser by Feller](https://wiser.feller.ch/de/professionals).

## Supported Devices

-   Wiser switchable light 1-channel #3401
-   Wiser switchable light 2-channel #3402
-   Wiser blind switch 1-channel #3404
-   Wiser blind switch 2-channel #3405
-   Wiser LED-universaldimmer 1-channel #3406
-   Wiser LED-universaldimmer 2-channel #3407
-   Wiser DALI-Dimmer 1-channel #3411

## Usage

### Connect the Embedded Web Interface from Wiser-by-Feller WLAN device

Еven without the mobile app, Wiser-by-Feller WLAN device can be set and controlled through a browser and WiFi connection of a mobile phone, tablet or PC (please make sure, that the device is not connetced to the cloud service -> see reset guideline in the manual of the device).

Installation procedure:

1. Install Wiser-by-Feller WLAN device
2. After first connection to power, Wiser-by-Feller WLAN device has created an own WiFi network, with name (SSID) such as `wiser-000xxxxx`. Connect to it with your phone, tablet or PC and enter passwort, provided together with the device (sticker).
3. Type `192.168.0.1` in your browser
4. Fill in `New Registration` and press the button on the device to continue
5. Log in
6. Go to `settings` -> `Network settings` -> `Get authentification tokenGet authentification tokenAdd new WLAN`
7. Enter your credentials and press button `Add WLAN`
8. Press button `Reboot Now!`
9. Log out and discconnect your phone, tablet or PC from the Wiser-by-Feller WLAN device
10. Get IP-Address of Wiser-by-Feller WLAN device in your router
11. Enter `IP-Adress` of Wiser-by-Feller WLAN device in settings of ioBroker.wiserbyfeller adapter instance `Gateway-IP`
12. Enter `username` of Wiser-by-Feller WLAN device in settings of ioBroker.wiserbyfeller adapter instance `username`
13. Click `save` button
14. Click `Get authentification token` button and follow the shown procedure
15. Click `close` button

## Controls

### Wiser Switchable Light

To turn on or off a load set the attribute `BRI` (brightness) to the following values:

-   Turn off set the `.ACTIONS.BRI` attribute to `off`
-   Turn on set the `.ACTIONS.BRI` attribute to `on`

### Wiser Blind Switch

On a motor e.g. shutter/blind you can set the target level between 0% and 100% (`0` - `10000`) and a tilt value.

-   To set the shutter in open position set the `.ACTIONS.LEVEL` attribute to `0`
-   To set the shutter in close position set the `.ACTIONS.LEVEL` attribute to `10000`
-   To control the shutter set the `.ACTIONS.LEVEL` attribute between `1` and `10000` (e.g. set `.ACTIONS.LEVEL` to `5000`, means set the shutter/blind to position 50%)
-   To control slats of a shutter (number of tilt) set the `.ACTIONS.TILT` attribute to a value `0` - `9`. Finally it's the motor running time, because we don't know the slat position in degrees.
-   To control the position and the tilt attribute together, set the `.ACTIONS.leveltilt.SET` attribute to value `true`. The shutter/blind will move to the position of the two values `.ACTIONS.leveltilt.level` and `.ACTIONS.leveltilt.tilt`

### Wiser LED-Universaldimmer

On a dimmable light you can set the target brightness between 0% and 100% (`0` - `10000`).

-   Turn off set the `.ACTIONS.BRI` attribute to `0`
-   To dim set the `.ACTIONS.BRI` attribute between `1` and `10000` (e.g. set `.ACTIONS.BRI` to `5000`, means 50% of brightness)

### Wiser DALI-Dimmer configured default (normal mode)

On a dimmable light you can set the target brightness between 0% and 100% (`0` - `10000`).

-   Turn off set the `.ACTIONS.BRI` attribute to `0`
-   To dim set the `.ACTIONS.BRI` attribute between `1` and `10000` (e.g. set `.ACTIONS.BRI` to `5000`, means 50% of brightness)

### Wiser DALI-Dimmer configured tw (Tunable-White)

On a dimmable light you can set the target brightness between 0% and 100% (`0` - `10000`).

-   Turn off set the `.ACTIONS.BRI` attribute to `0`
-   To dim set the `.ACTIONS.BRI` attribute between `1` and `10000` (e.g. set `.ACTIONS.BRI` to `5000`, means 50% of brightness)
-   To change the color set the `.ACTIONS.CT` attribute between `1000` and `20000`

### Wiser DALI-Dimmer configured rgb (RGBW red-green-blue-white)

On a dimmable light you can set the target brightness between 0% and 100% (`0` - `10000`).

-   Turn off set the `.ACTIONS.BRI` attribute to `0`
-   To dim set the `.ACTIONS.BRI` attribute between `1` and `10000` (e.g. set `.ACTIONS.BRI` to `5000`, means 50% of brightness)
-   To change the color set the `.ACTIONS.RED`, `.ACTIONS.GREEN`, `.ACTIONS.BLUE` and/or `.ACTIONS.WHITE` attribute between `0` and `255`

## Jobs

Create a two new jobs and connect them to two smartbuttons with `true` and `false`:

1. Open `[IP-Adress of Wiser-by-Feller WLAN device]/debug/apiui.html`
2. Click `Authorize` button
3. Enter value `SecretAuth (http, Bearer)`
4. Click `Authorize` button
5. Click `Close` button
6. Goto `POST api/system/flags`, click `Try it out` button
7. Enter `{"symbol": "cleaning", "value": true, "name": "[enter your command name]"}`
8. Click `Execute` button
9. Write down the ID
10. Goto `POST api/jobs`, click `Try it out` button
11. Enter `{"flag_values": [{"flag": [enter ID from step 9], "value": false}]}` in the Request body
12. Click `Execute` button
13. Write down the ID
14. Goto `POST api/jobs` again
15. Enter `{"flag_values": [{"flag": [enter ID from step 9], "value": true}]}` in the Request body
16. Click `Execute` button
17. Write down the ID
18. Goto `GET api/jobs/{id}}/setflags`, click `Try it out` button to test your first job
19. Enter the `id` of step 13
20. Goto `GET api/jobs/{id}}/setflags`, click `Try it out` button to test your second job
21. Enter the `id` of step 17
22. Connect the first job with the first scene SmartButton on your WiserByFeler-Device: Goto `POST api/smartbutton/program`, click `Try it out` button
23. Enter `{"on": true, "timeout": 60, "button_type": "scene", "owner": "user"}` in the Request body to set the WiserByFeller-Device in the programming mode
24. Click `Execute` button
25. Goto `GET api/smartbutton/notify`, click `Try it out` button
26. Click `Execute` button
27. Press a blinking Scene Button on your WiserByFeller Device
28. Write down the ID of the Button
29. Goto `PATCH api/smartbutton/{id}`, click `Try it out` button
30. Enter the button ID from step 28
31. Enter `{ "job": [job ID from step 9]}` in the Request body
32. Click `Execute` button
33. Connect the second job with the second scene SmartButton on your WiserByFeler-Device: Goto `POST api/smartbutton/program`, click `Try it out` button
34. Enter `{"on": true, "timeout": 60, "button_type": "scene", "owner": "user"}` in the Request body to set the WiserByFeller-Device in the programming mode
35. Goto `GET api/smartbutton/notify` again , click `Try it out` button
36. Click `Execute` button
37. Press a blinking Scene Button on your WiserByFeller Device
38. Write down the ID of the Button
39. Goto `PATCH api/smartbutton/{id}`, click `Try it out` button
40. Enter the button ID from step 36
41. Enter `{ "job": [job ID from step 13]}` in the Request body
42. Click `Execute` button
43. Restart ioBroker.wiserbyfeller adapter in the instance tab.
44. In the objects tab `wiserbyfeller.0.jobs.[ID]` should now an Object appear which can be toggeled `true` / `false` with the two scene SmartButtons

## Changelog

<!-- ### __WORK IN PROGRESS__ -->

### 0.1.0-beta.1

-   (ice987987) BREAKING: js-controller >= v4.0.23 and admin >= v6.2.19 is required
-   (ice987987) dependencies updated
-   (ice987987) section "disclaimer" in readme added
-   (ice987987) ukrainian language added
-   (ice987987) support for DALI-Dimmer added
-   (ice987987) additional device info added (folder: `.info.device.[...]`)
-   (ice987987) jobs added (folder: `.jobs.[...]`)

### 0.0.4 (12.03.2022)

-   (ice987987) cleartimeout added

### 0.0.3 (11.03.2022)

-   (ice987987) WebSocket connection to get values of the devices implemented
-   (ice987987) all subscribed states are now capitalized
-   (ice987987) new way to set leveltilt values added
-   (ice987987) readme updated

### 0.0.2 (27.02.2022)

-   (ice987987) description of several datapoints updated
-   (ice987987) icons for main datapoints added
-   (ice987987) license year updated
-   (ice987987) DP rssi into info-folder moved
-   (ice987987) readme.md updated
-   (ice987987) dependencies updated

### 0.0.1 (28.12.2021)

-   (ice987987) initial release

## License

MIT License

Copyright (c) 2023 ice987987 <mathias.frei1@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
