# Maizeless

<img src="img/maizeless_logo.svg" alt="logo" width="100"/>

Maizeless is a split, wireless-only, choc-spaced, diodeless mechanical keyboard, for use with the much-cheaper nice!nano clone, the [SuperMini nrf52840](https://wiki.icbbuy.com/doku.php?id=developmentboard:nrf52840).

## Lineage

Maizeless is closely related to the [Corne](https://github.com/foostan/crkbd), but without the maze of a row and column diodes (hence the name). Probably the closest description of it is a wireless [Cantor](https://github.com/diepala/cantor) (AirCantor, if you will?), or a diodeless [Swept Corne](https://github.com/AYM1607/swept-crkbd).

Going from matrix+diodes to direct pin was only possible with the extra 3 pins of the nice!nano (and clones) and giving up the TRRS pin, so this board is wireless only.

Genealogically speaking, it is forked from the [temper](https://github.com/raeedcho/temper), owing its starting shape and schematic to those pcb files. 

## Features

- 42-key split keyboard with 3 rows x 6 columns + 3 thumb keys per half 
- No diodes
- Kailh choc spacing
- Sweep-like column stagger (with pinky columns 2 mm lower, like chocofi) with Corne-like thumb cluster
- Reversible PCB (so one design can be used for both halves)
- Intended to be used with [SuperMini nrf52840](https://wiki.icbbuy.com/doku.php?id=developmentboard:nrf52840)
- Uses a dirt-cheap 3-pin [SS12D00 SPDT power switch](https://vimex.com/switches/techdocs/SS12D00-tech.pdf), of which 
- Includes pads for battery on keyboard shield PCB, and
  through-hole
- Easy and cheap to assemble, no soldering diodes and only through-hole
  soldering.
- (non-feature) - awkward battery positioning, and no JST plug. Not
  a big deal, just a heads up if you care.
- Trivial to alter the PCB design for:
  * 5 columns
  * use real nice!nanos (the 3 extra pins are in a sliiightly different position compared to the supermini).
  * add Kailh hotswap sockets to the PCB design, if you'd rather solder those to pads instead of direct through-hole soldering switches.

## Bill of Materials

- PCB x2
- 2x SuperMini nrf52840 microcontrollers
- 2x LiPo batteries (see nice!nano documentation for suggestions)
- 2x SS12D00 SPDT switches
- 42x Kailh choc v1 switches
- 42x Choc v1 keycaps
- (optional) MCU socket (more of a hassle than usual because we're
  using the extra 3 pins):
  - 4x Mill-Max 310 series machine sockets plus smaller ones for
    the extra 3 pins
  - 54x Mill-Max pins for socketing microcontrollers
- (optional) 2x Panasonic miniature momentary button switches  (for convenient reset buttons)

## Assembly

Assembly of this keyboard requires soldering the jumpers on the front-side of each PCB (underneath the microcontrollers). Past this, the assembly of this keyboard is similar to that of many other split wireless keyboards--there are many guides online to help. Briefly, the full list of steps includes:

- Solder the jumpers underneath the microcontrollers
- On PCB back:
  - Solder the diodes (ensuring diodes are oriented correctly--check diode schematic to match orientation to PCB)
  - Solder the switch sockets
- On PCB front:
  - Solder reset switch
  - Solder power switch
  - [Socket microcontroller](https://docs.splitkb.com/hc/en-us/articles/360011263059-How-do-I-socket-a-microcontroller-):
    - Solder sockets into PCB
    - Place masking tape (to divert solder from socket for next soldering step)
    - Insert Mill-Max pins or diode legs
    - Place microcontroller (blank side up)
    - Solder pins to microcontroller
    - Carefully remove microcontroller
    - Remove tape
  - (optional) socket nice!view displays (same procedure as socketing microcontroller)
  - *Carefully* solder battery wires to pads (ensuring wires don't short together--I used masking tape to secure wires)
  - (optional) For back plate: attach standoffs to PCB with screws
  - Press choc switches into sockets (ensuring that switch legs make it into the sockets and don't bend out of the way)
  - Place keycaps
  - Reseat microcontroller
- (optional) slide back plate onto standoffs and secure with screws
- (recommended) desolder SuperMini resistor that drains current for
  VCC output (since we aren't using it for LEDs).

## Firmware

This keyboard uses [ZMK firmware](https://zmk.dev), which allows for configuration through GitHub Actions. An example configuration repository is [here](https://github.com/raeedcho/temper-zmk-config.git).

## Resources

I adapted a few of the elements from these KiCAD libraries for use in this design:

- [chocofi](https://github.com/pashutk/chocofi) - The PCB switch layout came from the original chocofi design
- [kbd](https://github.com/foostan/kbd) - This library, by foostan, the designer of the popular Corne keyboard, provides useful schematic symbols and footprints
- [keyswitches.pretty](https://github.com/daprice/keyswitches.pretty) - library of switch footprints--especially useful for reversible PCBs.
- [swoop](https://github.com/jimmerricks/swoop) - Contains reversible PCB footprints for ProMicro pinout, OLED screens, and 7-pin power switches.


## Similar keyboards

There are many similar keyboards to this one. Here are some of the
closest; the original temper repo has a more complete list.

- [Corne/crkbd](https://github.com/foostan/crkbd) - A popular column stagger, 42-key split keyboard with many variants
- [Cornish Zen](https://lowprokb.ca/collections/keyboards/products/corne-ish-zen) - A low-profile wireless redesign of the Corne with choc spacing, screens, and an aluminum case
- [Fifi](https://github.com/raychengy/fifi_split_keeb) - 36-key split keyboard. Basically an MX Ferris Sweep with a Corne thumb cluster
- [Chocofi](https://github.com/pashutk/chocofi) - Choc version of the Fifi. Stagger is like the Kyria and Ferris keyboards, but with the pinky column 2mm lower. The keyboard this repository was based on.
- [temper](https://github.com/raeedcho/temper) - chocofi-based
  wireless-only split keyboard
- [Ferris Sweep](https://github.com/davidphilipbarr/Sweep) - Redesign of the Ferris for ProMicro MCU pinout, which also allows for a diodeless build. Many variations.
- [Swept Corne](https://github.com/AYM1607/swept-crkbd) - A wireless-only mix between the Corne and Ferris Sweep--basically a choc-spaced Corne with the Kyria pinky stagger (or alternatively a choc-spaced Kyria with a Corne thumb cluster)
- [Cantor](https://github.com/diepala/cantor) - 42 key wired
  keyboard, also diodeless thanks to the bountiful pins of the
  Blackpill.
