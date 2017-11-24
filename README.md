# homebridge-rcswitch-pulselength

The plugin is based on the idea of [FWeinb's rcswitch](https://github.com/FWeinb/homebridge-rcswitch) plugin.
It is written by Christopher Neuwirth, who named it Homebridge RC433 Etekcity plugin (https://github.com/ChristopherNeuwirth/homebridge-rc433-etekcity).
I bought switches at TOOM and they are manufactured by RWE. Normal rcswitch services were not working or
not working properly. The pulse length had to be set between 250 and 300 microsec. 350 or higher were not working.
Now the Etekcity plugin sets the pulse length originally to 188 microsec, which is too short, but as seen inssue no1
the original let specify a pulse length in the configuration file, but is not using this parameter.


# Installation

1. Install [WiringPi](https://projects.drogon.net/raspberry-pi/wiringpi/download-and-install/)
2. Install homebridge using: `npm install -g homebridge`
3. Install this plugin using: `npm install -g homebridge-rcswitch-pulselength`
4. Update your configuration file.

# Configuration

You can add as many switches as you like. You will need to pass the `name`, `id`=unitcode, `pulse` length,
the `on` and `off` code as decimal string as received by e.g. RFSniffer in the 433Utils.
This plugin assumes that you connect the 433Mhz transmitter to GPIO0.

 ```
 "accessories": [
     {
         "accessory": "RcSwitchP",
         "name": "Switch One",
         "id": "01",
         "pulse": "250",
         "on": "5566771",
         "off": "5577660"
     }
]
```
# Remarks

I added the pulselength feature into this easygoing plugin, because I bought switches at TOOM and they are manufactured by RWE.
These switches have a normal 1..5 and A..E coding, but were not switchable by rcswitch programm.
But I was able to switch my Brenstuhl switches with the remote of RWE (after coding), but not vice versa.
So I tried the platform-rcswitch, but this caused troulbe on my PI3.
(after changing the config, a restart of the homebridge is not enough, the Pi had to be restarted).
Nevertheless, it was possible to switch both types using a pulselength of 250 to 300 �s.
In the original homebridge-rcswitch it was not implemented to configure the pulselength.
