

# Resol VBus Adapter

## Goal

I have two Viessmann components that speak resol Vbus and 
I want to neatly integrate them into my home automation / monitoring.
And I also want to learn something along the way.

- The Viessmann [Vitotrans 353](https://www.viessmann.de/de/produkte/warmwasserbereiter/vitotrans-353.html)
is a controlled heat exchanger, that heats the tap water just in time for consumption to the desired temperature. 
The water stored in the reservoir will not reach the tap.
The control box is a re-branded Resol controller.

- For solar thermal energy collection, a "Vitosol" system is installed. 
The heat exchanger panels on the roof are connected to a "Solar Divicon" with a 
"Vitosolic 200" control box. Heat energy is collected and stored in a water reservoir. 
Again, this the controller is a re-branded [Resol Deltasol BX?](https://www.resol.de/de/produktdetail/69)



## available information

- Resol sells interface boxes https://www.resol.de/de/produktdetail/209 
- there is a discussion on Mikrocontroller.net https://www.mikrocontroller.net/topic/96431
- Chris at Hobbyelektronik has a similar [project with schematics](http://hobbyelektronik.org/w/index.php?title=VBus-Decoder)
- online, one can find the official Resol ["VBus-Protokollspezifikation.pdf"](https://hobbyelektronik.org/w/images/0/04/VBus-Protokollspezifikation.pdf) with a schematic on page 5

## My versions:

- [Version 0.0](vbusinterface_0.0/Readme.md)
- [Version 0.1](vbusinterface_0.1/Readme.md)
- [Version 0.2](vbusinterface_0.2/Readme.md)
- [Version 0.3](vbusinterface_0.3/Readme.md) (in development)


This is how the final system should look like. With options for USB-C and barrel-Jack power:
![IMG_20230901_124825](https://github.com/Dr-schobi/resol-vbus/assets/78444256/2055ccaa-9816-48e4-926d-14c37656a4cb)




