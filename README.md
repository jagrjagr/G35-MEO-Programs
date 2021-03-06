Addressable Holiday Lights
==========================

THIS IS *NOT* FOR GE G35 TYPE LIGHTS!!!

This is based on the new lights that showed up in the 2015 time frame with a ~103V V+ / ~100V V- supply and a data bus driven with two transistors. They go by names such as "Home Accents Holiday" (Home Depot), "Holiday Brightness" (Lowe's), and "Philips Pick-a-Color" (Target). The electronics for this are based off of TBJR6's work (https://hackaday.io/project/8933-addressable-christmas-lights-2015). Each board is a little different, but the same two transistors need isolated and connected to the digital outs of the Arduino. Powering the Arduino from the on board power is tricky. As TBJR6 states, it would be best to isolate the digital out pins of the Arduino with a opto-isolator and condition the Vcc+ on the board to protect the Arduino better.

This is heavily based on MarkEMarkEMark's (https://github.com/MarkEMarkEMark/G35-MEO-Programs) and sowbug's G35 Ardunino library (https://github.com/sowbug/G35Arduino). The idea was that these libraries are so well matured to update the core code that would be transparent to existing G35 programs out there.

This code is timer based and has the facility to manually change programs. At least 6 push buttons are required. It features a totally new MEOPrograms.cpp / .h with more imaginative programs from other light projects I've come across including my own original work and modifications.

This is preset for an Arduino Mega2560, but could easily be altered for other boards (sowbug has said that one program crashes his low memory board though). I am working on a ESP8266 additions in the near future to get rid of the horrid 433MHz RF remote.

Due to MarkEMarkEMark's modifications, the programs will no longer work with sowbug's originals, however his are easily modified to allow them to work once again.

For now, the remote does not work. 

Wiring
https://hackaday.io/project/8933-addressable-christmas-lights-2015

The programs and variations are, as follows:

- Whites: various simple whites
    - Warm White
    - Cold White
    - Warm and Cold White
    - Hint of RGB White
    - Hint of CYM White
- Rainbow: colour chasing with shades between (based on Adafruit's LED light strip sample code: https://github.com/adafruit/LPD8806)
    - Autumn Red & Green (spread across strings)
    - Ocean Green & Blue (spread across strings)
    - Pretty Blue & Red (spread across strings)
    - Full Rainbow (spread across strings)
    - Autumn Red & Green
    - Ocean Green & Blue
    - Pretty Blue & Red
    - Full Rainbow
    - Autumn Red & Green (interlaced direction)
    - Ocean Green & Blue (interlaced direction)
    - Pretty Blue & Red (interlaced direction)
    - Full Rainbow (interlaced direction)
- Random Stobe: Eiffel Tower at night type flashing effect
    - Black background / White flash
    - Blue background / White flash
    - Red background / White flash
    - Green background / White flash
    - Black background / Rainbow flash - each bulb flashes before colour change
    - Black background / Rainbow flash - colour changes with each flash
    - Rainbow background / white flash - colour changes gradually
    - Rainbow background / white flash - each background a different colour
- Simplex Noise: hard to describe - see original article - (based on happyinmotion's noise experiments http://happyinmotion.livejournal.com/278357.html)
    - Red, Green and Blue
    - Red and Blue
    - Green and Blue
    - Red and Green
    - Red
    - Green
    - Blue
    - Blue and dull Red
    - Blue and dull Green
    - Red and dull Green
    - Red and dull Blue
    - Green and dull Blue
    - Green and dull Red
- Sine Wave: creates a wave where the peaks are white, and the troughs are black (based on Adafruit's LED light strip sample code: https://github.com/adafruit/LPD8806)
    - Candystripe Red
    - Green
    - Blue
    - Yellow
    - Magenta
    - Cyan
    - Rainbow
    - Rainbow Graduated
- Chaser: This is a simple chase effect, but with nicer colour variations
    - Work in progress: Colour Cycle
    - Green Analogic
    - Red Analogic
    - Blue Analogic
    - Purply Blues
    - Valentines
    - Blue Triad
    - Blue Tetrad
    - Purple Tetrad
    - Green Tetrad
    - Red, Green, Blue & Yellow
    - Red, White & Blue
    - Red & Cyan
    - Green & Magenta
    - Blue & Yellow
    - Red, Cyan, Green, Magenta, Blue & Yellow
    - Red & Green
    - Green & Blue
    - Blue & Red
    - Cyan & Magenta
    - Magenta & Yellow
    - Yellow & Cyan
    - Red, Green & Blue
    - Cyan, Yellow & Magenta
    - Pastels
- Colour Phasing: hard to describe, but is an effect created by accident trying to do something else
    - Wavey pastels
    - Subtly changing pastels
    - White twinkle
    - Red/Cyan
    - Blue/Yellow
    - Green/Magenta
    - Red
    - Green
    - Blue
    - Ever evolving pastel wave
    - Still pastel rainbow
- Dither:
    - Red to Green
    - Green to Blue
    - Blue to Red
    - Colour Wheel smooth
    - Colour Wheel jump
    - Always changing
- Oscillate: like a pendulum - work in progress (disabled)

There are parameters that I've allowed for that I'll eventually make into sub-variations on other buttons

- MEORainbow
    - wait_: how fast/slow
    - frame_ : spread across string
    - type_: 0 to 3 - 0 is full rainbow. 1 is a nice autumnal red/green. 2 is green/blue. 3 is blue/red 
- MEORandomStrobe
    - noAtATime_ : how many simultaneous lights (don't do too many - between 1 and 5 is good)
    - colorMain_ : background colour (a nice start is dark blue - COLOR(0,0,4))
    - colorFlash_ : the flashing colour (try COLOR(15,15,15))
    - rainbowFlash_ : overrides colorFlash with a gradual colour cycle
    - rainbowFrame_ : if using rainbowFlash, will either change colour with each light flash, or when all bulbs have flashed
    - wait_ : how fast/slow
- MEOSimplexNoise
    - rMult/gMult/bMult_ - how much RGB to use (0.0 to 1.0)
- MEOSineWave
    - wavesPerString_: which harmonic (i.e. waves per string)
    - colorMain_ : the main colour to use (e.g. COLOR(15,0,0))
    - colorHi_ : the peak of the wave (e.g. COLOR(12,12,12))
    - colourLo_ : the trough of the wave (e.g. COLOR(0,0,0)) - these colours give a nice candy strip effect
    - rainbowMain_: parameter which rainbow cycles colorMain
- MEOColorPhasing
- MEOChasing
    
Feel free to email me if you have any problems setting up.

Thanks to sowbug (Mike Tsao) and, of course, Robert Quattlebaum (DeepDarc - http://www.deepdarc.com/2010/11/27/hacking-christmas-lights/) and Scott Harris and Paul Martis
