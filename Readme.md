

### Resol VBus Adapter

# Goal

I have two Viessmann components that speak resol Vbus and 
I want to neatly integrate them into my home automation / monitoring.
And I also want to learn something along the way.

- The Viessmann Vitotrans 353 [https://www.viessmann.de/de/produkte/warmwasserbereiter/vitotrans-353.html] 
is a controlled heat exchanger, that heats the tap water just in time for consumption to the desired temperature. 
The water stored in the reservoir will not reach the tap.
The control box is a re-branded Resol controller.

- For solar thermal energy collection, a "Vitosol" system is installed. 
The heat exchanger panels on the roof are connected to a "Solar Divicon" with a 
"Vitosolic 200" control box. Heat energy is collected and stored in a water reservoir. 
Again, this the controller is a re-branded Resol Deltasol BX? [https://www.resol.de/de/produktdetail/69]



# available information

- Resol sells interface boxes https://www.resol.de/de/produktdetail/209 
- there is a discussion on Mikrocontroller.net https://www.mikrocontroller.net/topic/96431
- Chris at Hobbyelektronik has a similar project with schematic http://hobbyelektronik.org/w/index.php?title=VBus-Decoder
- online, one can find the official Resol "VBus-Protokollspezifikation.pdf" https://hobbyelektronik.org/w/images/0/04/VBus-Protokollspezifikation.pdf with a schematic on page 5


# Version 0.0 (maybe from 2016?)

Components:
- USR TCP232 module for serial to Ethernet conversion https://www.pusr.com/products/1-port-rs232-to-ethernet-converters-usr-tcp232-302.html
(for about 20€ on Aliexpress)
- A TTL to RS232 converter board
- hand soldered PCB, following the schematic from Resol 
![IMG_20230901_115626](https://github.com/Dr-schobi/resol-vbus/assets/78444256/e9ebef80-0112-49d5-b2c3-9205fb914017)
![IMG_20230901_115753](https://github.com/Dr-schobi/resol-vbus/assets/78444256/de92feee-4d70-4bad-a6df-e9336e0d9bee)
![IMG_20230901_115800](https://github.com/Dr-schobi/resol-vbus/assets/78444256/2a75ff28-f2f8-48ba-b455-bd78f289b375)

The overall setup looks like this, with the two wall power adapters.

![IMG_20230901_115730](https://github.com/Dr-schobi/resol-vbus/assets/78444256/2258eb79-a6f3-43dc-b7ed-6930629828da)


Note: Inside the USR-TCP232 there is a convenient place (upper left) for a solder bridge (or fuse, I didn't have one) to output 5V on the DB9 connector.
This is used for powering my electronics.

![IMG_20230901_115956](https://github.com/Dr-schobi/resol-vbus/assets/78444256/4d210825-c006-4a13-bbe0-bbf098e969ba)

As we can see, the signal is converted from TTL to RS232 (outside) and back from RS232 to TTL inside the TCP232. This seemed quite unnecessary.

![IMG_20230901_120029](https://github.com/Dr-schobi/resol-vbus/assets/78444256/868debb4-9ce1-46bc-a75b-e11a2177872e)

Conclusion:
- this worked fine and I could intergrate the software and start using the data.
- The mess of wires hanging from the IT rack were annoying but lasted for quite some time. A more compact solution with proper housing was needed

# Version 0.1 (about 2017)

