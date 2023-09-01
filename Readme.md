

# Resol VBus Adapter

## Goal

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



## available information

- Resol sells interface boxes https://www.resol.de/de/produktdetail/209 
- there is a discussion on Mikrocontroller.net https://www.mikrocontroller.net/topic/96431
- Chris at Hobbyelektronik has a similar project with schematic http://hobbyelektronik.org/w/index.php?title=VBus-Decoder
- online, one can find the official Resol "VBus-Protokollspezifikation.pdf" https://hobbyelektronik.org/w/images/0/04/VBus-Protokollspezifikation.pdf with a schematic on page 5


## Version 0.0 (maybe from 2016?)

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
Also, for two systems, I might not need two power supplies?

![IMG_20230901_120029](https://github.com/Dr-schobi/resol-vbus/assets/78444256/868debb4-9ce1-46bc-a75b-e11a2177872e)




Conclusion:
- this worked fine and I could intergrate the software and start using the data.
- The mess of wires hanging from the IT rack were annoying but lasted for quite some time. A more compact solution with proper housing was needed

## Version 0.1 (about 2017)

Changes:
- I always wanted to make some more PCBs, this time using SMD technology to make it smaller (I can't remember why "smaller" was a requirement)
- There is a more compact and cheaper USR TCP232-T2 module available https://www.pusr.com/products/serial-to-ethernet-converter-modules-usr-tcp232-t2.html  (about 10€)
![IMG_20230901_123149](https://github.com/Dr-schobi/resol-vbus/assets/78444256/f3e1c038-ca4d-4cdd-bef8-e8c990c533c8)

In the end I got some working PCBs that were not installed and put on hold for a few years.

![IMG_20230901_123143](https://github.com/Dr-schobi/resol-vbus/assets/78444256/9c26b1bf-bbf7-4faa-ad52-4b2c47f75851)
![IMG_20230901_123122](https://github.com/Dr-schobi/resol-vbus/assets/78444256/9d6cbcab-b989-46a4-854b-462f34e01356)

Conclusion:
- this did not include any mounting options. Wiring with pin headers is fine for experimenting, but not any better for isntallation
- powering with 3.3V did not work properly, so I had to re-wire for 5V

## Version 0.2 (2023-08)

I came across the box of materials and decided to finish this project.
The wires of the flying installation verion 0.0 have broken off in the meantime and the system was not operational.

Changes:
- re-draw with a new Kicad version (I would say I haven't lost them, but I stopped searching for the old files)
- integrate connectors, use Wago 2604-1102 [https://www.wago.com/global/pcb-terminal-blocks-and-pluggable-connectors/pcb-terminal-block/p/2604-1102]
- try to have it mostly assembled from JLCPCB to avoid stocking 10s of some exotic components
- use an off-the shelf PoE splitter for providing the 5V without extra power supplies, option of barrel jack or micro-USB power connector
- integrate a mounting system, I decided to use the Phoenix Contact UMK system to have a DIN rail mount for everything. This requires [UMK-BE22.5](https://www.phoenixcontact.com/en-pc/products/base-element-umk-be-225-2970028), [UMK-SE11,25-3](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-3-5030266), [UMK-11,25-1](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-1-2970442) and [UMK-FE](https://www.phoenixcontact.com/en-pc/products/foot-element-umk-fe-2970031). This is a really cool configurable system which results in a really neat and sturdy mounting. (RANT:) However, the Phoenix Contact Website is completely useless for selecting which components one might want to use. There is not "compatible with" indication, no online configurator, not even a small quantity ordering process. I'm sure when I call them from my day-job, a representative will show up immediately and explain the system to me. But as a hobbyist, this is unreachable and more expensive than the assembled PCB. Sorry, but you've scared me away for any future use even in my day-job.

![IMG_20230901_125111](https://github.com/Dr-schobi/resol-vbus/assets/78444256/bc277ec8-eeb2-4661-8a2c-95891a0dd32e)

really nice partially assembled PCBs as they arrived from JLCPCB
![IMG_20230901_124908](https://github.com/Dr-schobi/resol-vbus/assets/78444256/1446f227-5885-446d-a52a-b3ef9452ed5f)

![IMG_20230901_124859](https://github.com/Dr-schobi/resol-vbus/assets/78444256/4262b4da-9dba-4948-8681-8e889303e219)

not so nice any more - with the needed fixes integrated

![IMG_20230901_124851](https://github.com/Dr-schobi/resol-vbus/assets/78444256/78fe05ab-db61-40ea-951e-3391c4186dff)

This is how the final system should look like. With options for USB-C and barrel-Jack power:
![IMG_20230901_124825](https://github.com/Dr-schobi/resol-vbus/assets/78444256/2055ccaa-9816-48e4-926d-14c37656a4cb)


![IMG_20230901_124807](https://github.com/Dr-schobi/resol-vbus/assets/78444256/30b18e25-a75a-424e-893c-40141d326ee2)


Errata:




