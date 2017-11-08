# homebridge-rcswitch-pulselength

Add support for rc switches using [rcswitch](https://github.com/marvinroger/node-rcswitch)

# Installation

1. Install [WiringPi](https://projects.drogon.net/raspberry-pi/wiringpi/download-and-install/)
2. Install homebridge using: `npm install -g homebridge`
3. Install this plugin using: `npm install -g homebridge-rcswitch`
4. Update your configuration file.

# Configuration

You can add as many switches as you like. You will need to pass the `name`, `systemcode` and `unitcode`.
This plugin assumes that you connect the 433Mhz transmitter to GPIO0, this can be changed via the `pin` property. 
Additional the pulslength of the signal could be changed. If you do not specify it will be set to 300 µs.

 ```
 "accessories": [
     {
       "accessory": "RcSwitch",
       "name": "Switch One",
       "systemcode": "11101", 
       "unitcode": 1,
       "nPulseLength": 250,
       "pin": 0
     }
]
```
# Remarks

I added the pulselength feature into this easygoing plugin, because I bought switches at TOOM and they are manufactured by RWE. 
These switches have a normal 1..5 and A..E coding, but were not switchable by this programm.
But I was able to switch my Brenstuhl switches with the remote of RWE (after coding), but not vice versa.
So I tried the platform-rcswitch, but this caused troulbe on my PI3.
(after changing the config, a restart of the homebridge is not enough, the Pi had to be restarted).
Nevertheless, it was possible to switch both types using a pulselength of 250 to 300 µs.
In the original homebridge-rcswitch it was not implemented to configure the pulselength.