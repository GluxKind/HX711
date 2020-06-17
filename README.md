# HX711

Arduino library for HX711 24 bit ADC  used for load cells and scales.

# Description

This HX711 library has an interface which is a superset of a library made by bogde.
Some missing functions were added to get more info from the lib. 

Another important difference is that this library uses floats. The 23 bits mantisse 
of the IEE754 float matches the 24 bit ADC very well. Furthermore it gave a smaller
footprint. 

**Main flow**

First action is to call **begin(DATAPIN, CLOCKPIN)** to make connetion to the **HX711**.

Second step is callibration for which a number of functions exist.
* **tare()** measures zero point
* **set_scale(factor)** set a known conversion factor e.g. from EEPROM.
* **callibrate_scale(WEIGHT, TIMES)** determines the scale factor based upon a known weight e.g. 1 Kg.

Steps to take for callibration
1. clear the scale
1. call tare() to set the zero offset
1. put a known weight on the scale 
1. call callibrate_scale(weight) 
1. scale is calculated.
1. save the offset and scale for later use e.g. EEPROM.


**Pricing**

Some price functions were added to make it easy to use this library
for pricing goods or for educational purposes. These functions are under discussion
if they will stay. Another set of function to add weights together didn't make it in 
the 0.2.0 release, it is on a todo list.

**weight.h"
Weight.h is a separate include file with a number of weight conversion functions.
Could become a repository in itself one day.

```
          stone - lbs - ounce
            |      |      |
           kilo   kilo - gram
```
Overview conversions in weight.h


## Notes

**Scale values for loadcells**

These scale values worked pretty well with a set of loadcells, 
Use callibrate to find your values.

* 5 KG loadcell   scale.set_scale(420.52); 
* 20 KG loadcell  scale.set_scale(127.15); 

**Connections HX711**

A+/A-  uses gain of 128 or 64
B+/B-  uses gain of 32

**Connections**

| HX711 Pin | Color |
|:----|:----|
| E+ | rood          | 
| E- | zwart         | 
| A- | wit           | 
| A+ | groen         | 
| B- | not connected | 
| B+ | not connected | 


| HX711 Pin | Color |
|:----|:----|
| E+ | rood          |
| E- | zwart         |
| A- | blauw         |
| A+ | wit           |
| B- | not connected |
| B+ | not connected |

## Operation

See examples
