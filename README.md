# Leafspa
Read and Store readings of:
- CO2 level
- Temperature
- Relative Humidity

Manage the level of:
- CO2
- Water vapor (relative humidity level)

# Intro
This is my first node-red app.  I am not sure if I will ultimately choose node-red for this project or eventually switch to a microcontroller / CircuitPython environment.  What I am finding is great about node-red is its ability to rapidly implement a design intent through a flow.  It is thrilling to work out a code flow - just as I would with a flow diagram - and then tweak as needed.  It has afforded rapid prototyping.  So for prototyping, I am really enjoying node-red.  However, tbe high level of abstraction provided by node-red - while very much appreciated for prototyping - might be too much for a deployed system.  When I want something to run consistently, I tend to want a much more simplified microcontroller environment.  So we will see.

# Learnings
## Relays
### First Try - Kasa Smart Power Strip (HS300)
#### Good
- Both node-red and Python can use the TP-Link APIs ([GitHub for the APIs](https://github.com/plasticrake/tplink-smarthome-api), [node-red API page](https://flows.nodered.org/node/node-red-contrib-tplink) to control the power switch.
- Kasa has an app for iPhone/Android that lets us set a schedule for a plug (useful for the LED), view if a plug is on/off, and turn on/off a plug.
#### Not so good
- Several of the API calls get a TCP Timeout error.  I have not tracked this down as much as I perhaps should.  The node-red puts an abstraction above the APIs, and I have not spent enough time isolating this. __TBD__
- Unclear if the continual turning on and off damages the relays.

### Second Try - separate relays
I just ordered two [enclosed relays](https://smile.amazon.com/gp/product/B017743I7S/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1) I like that these can be directly attached and are isolated.  This should be a simpler approach for items that are turned off/on based on a sensor measurement.