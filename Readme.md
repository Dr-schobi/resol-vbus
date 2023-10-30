

# Resol VBus Adapter

## Goal

I have two Viessmann components that speak Resol Vbus and 
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


## Version overview
- [Version 0.0 (maybe from 2016?)](https://github.com/Dr-schobi/resol-vbus/tree/main/vbusinterface_0.0)
- [Version 0.1 (about 2017)](https://github.com/Dr-schobi/resol-vbus/tree/main/vbusinterface_0.1)
- [Version 0.2 (2023-08)](https://github.com/Dr-schobi/resol-vbus/tree/main/vbusinterface_0.2)
- [Version 0.3 (2023-08)](https://github.com/Dr-schobi/resol-vbus/tree/main/vbusinterface_0.3)

## Results

final layout and schematic
![layout](https://github.com/Dr-schobi/resol-vbus/assets/78444256/c10df4cb-5788-43fc-90e1-fe1d461f41bc)
![schematic](https://github.com/Dr-schobi/resol-vbus/assets/78444256/377a6e99-267e-473f-8a9d-84cf58419b6b)

and finally mounted to the wall, hidden away in a corner
![mounted](https://github.com/Dr-schobi/resol-vbus/assets/78444256/02f6e7a4-8c2a-4910-a849-214dd1b3b6c5)

USR-TCP232-T2 setup:
- new modules come with admin/admin and IP 192.168.0.7
- login via browser and set your IP, set serial port 9600 baud, TCP server with port 8234
- do not try to remove the password! setting an empty password will break the modules

My home automation software is based on EDOMI, with a python module for accessing and logging, see https://knx-user-forum.de/forum/projektforen/edomi/1125369-lbs-resol-vbus-viessmann-vitosol-200

This is the values I'm currently getting from the systems. Still a long way to go in understanding them.
![values](https://github.com/Dr-schobi/resol-vbus/assets/78444256/637b99a4-dcd3-4fa8-8ecf-b538f5ed11d4)


