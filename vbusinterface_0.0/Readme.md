
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
