# Welcome to the Leafspa project
I'm glad to meet you.  Umm...although I am doubtful my rambling learnings will be that useful to you.  

I am embarking on a journey to grow medicinal plants.  I will do this both indoors and outdoors.  I want to grow indoors because I enjoy being around growing plants.  I lose this enjoyment as the summer dwindles to an end and the wet, cold, dark invades for about half the year.

I love to learn by doing.  Thus, this project.  This project is a prototype to evolve my knowledge on building an automated indoor grow environment where the ideal levels of environmental factors for plants is automatically maintained. 
## Environmental factors
Environmental factors I can automate the management of include:
- The photoperiod of the LEDs.
- The amount of CO2.
- The amount of humidity.
- The temperature.

### Managing the photoperiod
When possible, keep things simple. To set the number of hours the LEDs are on, I use a mechanical timer like [this one](https://amzn.to/38KqBeg).  One less thing that could go wrong!
### Managing other environmental factors
I have focused my effot on automating the amounts of CO2 and humidity. CO2 too low? Turn on the CO2 tank until it isn't.  Humidity too low? Turn on the humidifier then turn it off when the relative humidity is where I want it... I could manage the temperature, but decided against doing so because the temperature without any management ranges between 76-80 degrees during the time the LEDs are on and 70 - 68 degrees when the lights are off.
### Analyze
I store the values for CO2, relative humidity, and temperature and then view graphs of different time periods to understand what the values were while I was off galavanting around.
# Leafspa
Read and Store readings of:
- CO2 level
- Temperature
- Relative Humidity

Manage the level of:
- CO2
- Water vapor (relative humidity level)

__TODO: I am in process__

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