
## Version 0.2 (2023-08)

While cleaning up, I came across the box of materials and decided to finish this project.
The wires of the flying installation verion 0.0 have broken off in the meantime and the system was not operational.
![pcb](https://github.com/Dr-schobi/resol-vbus/assets/78444256/260480eb-3ebd-41ad-b61a-77132e92150d)
![schematic](https://github.com/Dr-schobi/resol-vbus/assets/78444256/4b2488a4-bd58-438f-9830-35919e05ab5b)

Changes:
- re-draw with a new Kicad version (I would say I haven't lost them, but I stopped searching for the old files)
- integrate connectors, use [Wago 2604-1102](https://www.wago.com/global/pcb-terminal-blocks-and-pluggable-connectors/pcb-terminal-block/p/2604-1102)
- try to have it mostly assembled from JLCPCB to avoid stocking 10s of some exotic components
- use an off-the shelf PoE splitter for providing the 5V without extra power supplies, option of barrel jack or micro-USB power connector
- integrate a mounting system, I decided to use the Phoenix Contact UMK system to have a DIN rail mount for everything. This requires [UMK-BE22.5](https://www.phoenixcontact.com/en-pc/products/base-element-umk-be-225-2970028), [UMK-SE11,25-3](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-3-5030266), [UMK-11,25-1](https://www.phoenixcontact.com/en-pc/products/side-element-umk-se-1125-1-2970442) and [UMK-FE](https://www.phoenixcontact.com/en-pc/products/foot-element-umk-fe-2970031). This is a really cool configurable system which results in a really neat and sturdy mounting. (RANT:) However, the Phoenix Contact Website is completely useless for selecting which components one might want to use. There is not "compatible with" indication, no online configurator, not even a small quantity ordering process. I'm sure when I call them from my day-job, a representative will show up immediately and explain the system to me. But as a hobbyist, this is unreachable and more expensive than the assembled PCB. Sorry, but you've scared me away for any future use, even in my day-job.

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
