# Welcome to the Leafspa project


 __This project is a prototype__ to evolve my knowledge on building an automated indoor grow environment where the ideal levels of environmental factors for plants is automatically maintained. The goal of this project is simple.  The main focus of this project is the management of CO2 and humidity levels within a grow tent.
## Environmental factors
Environmental factors I can automate the management of include:
- The airflow.
- The photoperiod of the LEDs.
- The amount of CO2.
- The amount of humidity.
- The temperature.

### Managing the airflow
Who wants mildew on their plants?  I don't.  So I set up 12V fans out of old PCs.  Nothing fancy here.  They are strung about and on all the time.  I don't measure the airflow.  My thinking is as long as I can see the leaves move slightly because of wind all is good.

### Managing the photoperiod
When possible, keep things simple. To set the number of hours the LEDs are on, I use a mechanical timer like [this one](https://amzn.to/38KqBeg).  One less thing that could go wrong!
### Managing CO2 and Humidity
I have focused my efforts on automating the amounts of CO2 and humidity. CO2 too low? Turn on the CO2 tank until it isn't.  Humidity too low? Turn on the humidifier then turn it off when the relative humidity is where I want it... 
### Managing Temperature
I could manage the temperature, but decided against doing so because the temperature without any management ranges between 76-80 degrees during the time the LEDs are on and 70 - 68 degrees when the lights are off.
### Analyze
I store the values for CO2, relative humidity, and temperature and then view graphs of different time periods to understand what the values were while I was off galavanting around.
# Hardware and Software
Finally...we start talking about all the crap that causes a whole bunch of cords to be plugged into multiple extension cords...(sigh...cords..ugh...).
First the hardware.
## Hardware
- A __Raspberry Pi__ acts as the control center.  I started with a Zero W.  The Zero W is inadequate because it is underpowered to run the software I am using for this prototype.  Also, [the single core Armv6 makes it impossible to run the multicore packages that require the Armv7](https://raspberrypi.stackexchange.com/questions/83374/raspberry-pi-zero-w-is-armv6-or-armv7#:~:text=1%20Answer&text=First%3A%20It's%20ARMv6.,the%20ARMv6%20instruction%20set%20architecture.)
- An [SCD-30 CO2 sensor](https://www.adafruit.com/product/4867) that measures the CO2, temperature, and relative humidity levels. _Note: Since I started, I noticed the [SCD-40](https://www.adafruit.com/product/5187) which might be a better choice.  It's $10 less and smaller.  The challenge might be in library support.  But what are challenges? Just opportunities..._
- A homemade humidifier that uses a PC fan, a [mister](https://amzn.to/2VrlEE4), [container](https://amzn.to/38YlyH2), water tank that sits below the grow tent (the water tank was a left over from our van conversion.  It's just a big tank filled with water), and a submersible pump - something like [this on](https://amzn.to/2VtGPpb) although the water flow could be lower.  It's just a pump I had from a previous project. 
- Two [non contact water level sensors](https://amzn.to/3BWmhFs) that are positioned at spots on the container that correspond to the high and low water levels where the mister works.
- A CO2 tank and a [solenoid for the tank](https://amzn.to/2XdQvEZ) that allows me to turn the CO2 flow on and off.
- A [relay module](https://amzn.to/3zY3Krr) that I attached to 3 [wall outlets](https://www.homedepot.com/p/Leviton-15-Amp-Residential-Grade-Grounding-Duplex-Outlet-White-R52-05320-00W/202066670)

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