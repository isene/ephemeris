# Ephemeris

Ruby Class::Ephemeris

This is a complete ephemeris class for Ruby. The code can easily be used in
other languages or wrapped for use as a CLI application or on a web page.

The system is an implementation of [this in-depth
description](http://www.stjarnhimlen.se/comp/ppcomp.html#5) and with Jean
Meeus' "[Astronomical Formulae for
Calculators](https://www.amazon.com/Astronomical-Formulae-Calculators-Jean-Meeus/dp/0943396220/ref=sr_1_7?dchild=1&keywords=jean+meeus&qid=1608136572&sr=8-7)" as reference. The basic data from the in-depth description has been tweaked
somewhat to better fit our era.

Usage is simple and straightforward:

```
o = Ephemeris.new(date, lat, lon, tz)
```
...creates a new ephemeris object for the "date" (a string in ISO format `2020-12-16`)
by supplying the observer's latitude (lat), longitude (lon) and time zone (tz).

Example: `today = Ephemeris.new("2020-12-16", 59.568, 10.02, 1)`

You will then have access to the following data:

```
today.sun
today.moon 
today.mercury
today.venus
today.mars
today.jupiter
today.saturn
today.uranus
today.neptune
```

By calling any of these, you will get back an array with the following data:

```
[ra, dec, distance, ra_string, dec_string, rise, transit, set]
```
where:
```
ra         = object's Right Ascension (float)
dec        = object's Declination (float)
distance   = object's distance from Earth in AUs (float) - except for the Moon
ra_string  = ra in a presentable string, e.g "17h 24m 31s"
dec_string = dec in a presentable string, e.g "-24° 16´ 47˝"
rise       = object's time of rise above the horizon (float, fraction of 24h)
transit    = object's time of transit (float, fraction of 24h)
set        = object's time of setting (float, fraction of 24h)
```

You will also get access to the method "print" that will print out a nice
table with data fro the planets:

```
today.print

Planet  │ RA          │ Dec          │ Dist. │ Rise  │ Trans │ Set
────────┼─────────────┼──────────────┼───────┼───────┼───────┼──────
Mercury │ 17h 24m 31s │ -24° 16´ 47˝ │  1.44 │ 09:27 │ 12:02 │ 14:38
Venus   │ 15h 53m  7s │ -18° 57´ 29˝ │  1.50 │ 06:56 │ 10:31 │ 14:05
Mars    │  1h 16m 21s │   8° 34´ 10˝ │  0.75 │ 12:54 │ 19:54 │ 02:54
Jupiter │ 20h  4m 43s │ -20° 49´ 46˝ │  5.87 │ 11:27 │ 14:42 │ 17:58
Saturn  │ 20h  7m 11s │ -20° 35´ 38˝ │ 10.79 │ 11:27 │ 14:45 │ 18:03
Uranus  │  2h 18m 28s │  13° 20´ 44˝ │ 19.08 │ 13:19 │ 20:56 │ 04:33
Neptune │ 23h 17m 19s │  -5° 45´ 42˝ │ 29.99 │ 12:35 │ 17:55 │ 23:15
```
