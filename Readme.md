

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


## Version 0.0 (maybe from 2016?)

Components:
- use an existing serial to Ethernet conversion module [USR TCP232](https://www.pusr.com/products/1-port-rs232-to-ethernet-converters-usr-tcp232-302.html)
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
- I always wanted to make some proper more PCBs myself, this time using SMD technology to make it smaller (I can't remember why "smaller" was a requirement)
- There is a more compact and cheaper [USR TCP232-T2 module](https://www.pusr.com/products/serial-to-ethernet-converter-modules-usr-tcp232-t2.html)  available for about 10€
![IMG_20230901_123149](https://github.com/Dr-schobi/resol-vbus/assets/78444256/f3e1c038-ca4d-4cdd-bef8-e8c990c533c8)

In the end I got some working PCBs, but they did not get installed and put on hold for a few years.

![IMG_20230901_123143](https://github.com/Dr-schobi/resol-vbus/assets/78444256/9c26b1bf-bbf7-4faa-ad52-4b2c47f75851)
![IMG_20230901_123122](https://github.com/Dr-schobi/resol-vbus/assets/78444256/9d6cbcab-b989-46a4-854b-462f34e01356)

Conclusion:
- the PCB did not include any mounting options. Wiring with pin headers is fine for experimenting, but not any better for installation
- error on the PCB, powering with 3.3V did not work properly, so I had to re-wire for 5V

## Version 0.2 (2023-08)

While cleaning up, I came across the box of materials for this project and decided to finish this project.
The wires of the flying installation verion 0.0 have broken off in the meantime and the system was not operational.
![pcb](https://github.com/Dr-schobi/resol-vbus/assets/78444256/260480eb-3ebd-41ad-b61a-77132e92150d)
![schematic](https://github.com/Dr-schobi/resol-vbus/assets/78444256/4b2488a4-bd58-438f-9830-35919e05ab5b)

Changes:
- re-draw with a new Kicad version (I wouldn't say I have lost them, but I stopped searching for the old files)
- integrate connectors, use [Wago 2604-1102](https://www.wago.com/global/pcb-terminal-blocks-and-pluggable-connectors/pcb-terminal-block/p/2604-1102)
- try to have it mostly assembled from JLCPCB to avoid stocking 10s of some exotic SMD components
- use an off-the shelf PoE splitter for providing the 5V without extra power supplies, option of barrel jack or micro-USB power connector
- integrate a mounting system, I decided to use the Phoenix Contact UMK system to have a DIN rail mount for everything. This requires [UMK-BE22.5](https://www.phoenixcontact.com/en-pc/products/base-element-umk-be-225-2970028), [UMK-SE11,25-3](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-3-5030266), [UMK-11,25-1](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-1-2970442) and [UMK-FE](https://www.phoenixcontact.com/en-pc/products/foot-element-umk-fe-2970031). This is a really cool configurable system which results in a really neat and sturdy mounting. (RANT:) However, the Phoenix Contact Website is completely useless for selecting which components one might want to use. There is no "compatible with" indication, no online configurator, not even a small quantity ordering process. I'm sure when I call them in a commercial setting from my day-job, a representative will show up immediately and explain the system to me. But as a hobbyist, this is unreachable. Individual parts online are more expensive than the assembled PCB. Sorry Phoenix Contact, but you've scared me away for any future use, even in my day-job.

![IMG_20230901_125111](https://github.com/Dr-schobi/resol-vbus/assets/78444256/bc277ec8-eeb2-4661-8a2c-95891a0dd32e)

really nice partially assembled PCBs as they arrived from JLCPCB
![IMG_20230901_124908](https://github.com/Dr-schobi/resol-vbus/assets/78444256/1446f227-5885-446d-a52a-b3ef9452ed5f)

![IMG_20230901_124859](https://github.com/Dr-schobi/resol-vbus/assets/78444256/4262b4da-9dba-4948-8681-8e889303e219)

not so nice any more - with the needed fixes integrated

![IMG_20230901_124851](https://github.com/Dr-schobi/resol-vbus/assets/78444256/78fe05ab-db61-40ea-951e-3391c4186dff)

This is how the final system should look like. With options for USB-C and barrel-Jack power:
![IMG_20230901_124825](https://github.com/Dr-schobi/resol-vbus/assets/78444256/2055ccaa-9816-48e4-926d-14c37656a4cb)


![IMG_20230901_124807](https://github.com/Dr-schobi/resol-vbus/assets/78444256/30b18e25-a75a-424e-893c-40141d326ee2)

Conclusion:
- much nicer, but I introduced some errors
- when changing a few parts, even more can likely be assembled from "basic parts" directly, sparing me a load of new bags with individual SMD components

Errata:
- when designing a new component with Kicad, the default hole diameter is too small to fit a standard pin header. I had to use individual pieces of 0.4mm wire to mount my components U4 and U5
- the output to the TCP232 should be 3.3V only, but I was powering the 4093 stage with 5V. R3 needs to match. 
- for C1, I picked the wrong part from JLCPCB, should be 1nF instead of 1uF

(RANT on JLCPCB:) the JLCPCB parts selection is broken for me. For example, when searching for a "0805" resistor with a specific value, the parametric search does not gives too many results. When limiting to "basic parts" only, tjhe list is empty. Listing all "basic parts" "0805" resistors is possible, but they can't be sorted, the actual values in the list are cut off (I need to click though every part?). The Kicad Export with the Fabrication Toolkit is a really nice new way for single click export. But somehow the ICs are rotated the wrong way and the board dimensions for backside assembly are mixed up... In the end, this is still the best manufacturer for me, but I hesitate to pay more for shipping than for the product.


# Version 0.3 (2023-08)

Changes:
- small redesign from Errata above, 
- more basic parts assembled from JLCPCB
- 
![layout](https://github.com/Dr-schobi/resol-vbus/assets/78444256/c10df4cb-5788-43fc-90e1-fe1d461f41bc)
![schematic](https://github.com/Dr-schobi/resol-vbus/assets/78444256/377a6e99-267e-473f-8a9d-84cf58419b6b)


USR-TCP232-T2 setup:
- new modules come with admin/admin and IP 192.168.0.7
- login via browser and set your IP, set serial port 9600 baud, TCP server with port 8234
- do not try to remove the password! setting an empty password will break the modules




