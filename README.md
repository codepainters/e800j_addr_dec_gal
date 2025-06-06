# PROM replacement for Elwro 800 Junior - GAL16V8 variant

Elwro 800 Junior uses two `SN74S474` 512x8 PROMs as IO and memory address decoders. These PROMs are increasingly difficult to obtain (and program), this project provides a `GAL16V8`-based plug-in replacement for both address decoders. 

Note: there is [another version](https://github.com/codepainters/e800j_addr_dec_atf/) using `ATF1502ASL` CPLDs in TQFP-44, if you prefer SMD devices and JTAG programming :) 

![](img/addr_dec_gal_real.jpg)

Hardware files:

* [pcb](pcb) - schematic/PCB project in KiCAD 8 format
* PDF schematics - [color](pdf/addr_dec_gal.pdf) and [black&white](pdf/addr_dec_gal_bw.pdf)
* [interactive BOM](addr_dec_gal_ibom.html) file (you have to download it and open locally)
* Gerber files (in a [jlcpcb](https://jlcpcb.com/)-compatible ZIP format):
  * [addr\_dec\_gal.zip](gerbers/addr_dec_gal.zip) - single PCB
  * [addr\_dec\_gal\_panel.zip](gerbers/addr_dec_gal_panel.zip) - two PCBs panelized



PLD sources:

* [io](io) - source and JEDEC file for I/O address decoder
* [mem](mem) - source and JEDEC file for memory address decoder

Both decoders have been verified by comparing them against PROM dumps and tested to ensure they function correctly in the Elwro 800 Junior board.

The source files can be compiled with [galasm](https://github.com/daveho/GALasm) like e.g.:

```
$ galasm io.pld
```

Target `GAL16V8` can be programmed with a `.jed` file using `TL866A` or similar programmer.
