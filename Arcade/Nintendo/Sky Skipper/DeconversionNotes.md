# TNX-Converted Popeye Deconversion Notes
The goal of this document is to provide detailed documentation for deconverted a TNX board that currently plays Popeye.
This documentation is based off of the write-up done by Supergun on KLOV

Be aware that this is a technically involved deconversion. Do at your own risk. Read the instructions thoroughly before attempting.

## Required Components
- 4: 2532 EPROMs
- 7: 2732 EPROMs
- 2: 82S123 (or equivalent) bipolar ROMs
- 3: 82S129 (or equivalent) bipolar ROMs
- 1: 3.3k ohm resistor
- solder
- 30 gauge wire (or whatever you want to use for repairing traces)

## Required Tools
- Soldering iron (preferably with a fine tip)
- wire strippers (or method for stripping the wire used for repairing traces)
- small flathead screwsdriver or chip lifter
- programmer capable of burning required ROM ICs

## CPU PCB (TNX1-0*-CPU)
### ROM Replacement
There are eight 2732 EPROMs populated from 2A to 2H. These will need to be replaced with the seven Sky Skipper ROMs. Refer to the following table for more ROM info.

### Jumper Changes
Jumper J9 was set to closed for Popeye. It should be changed to **open/off** for Sky Skipper.

## Video PCB (TNX1-0*-VIDEO)
### ROM Replacement
There is one 2716 eprom on the video PCB. This will need to be replaced with the Sky Skipper ROM. 
## Tile Interface PCB (TNX1-0*-TIF)
### ROM Replacement
There are two daughterboards placed in the EPROM sockets on the TIF board. These will need to be removed along with the extra wire. Be aware that daughterboards are in there tight. It is encouraged to replace these sockets as 40+ years of oversized pins likely pushed the socket pins in too far to make proper EPROM connection.

In place of the daughterboards will be four **2532** EPROMs. Note that 2732 EPROMs will not work without board modifications, use 2532 instead. Refer to the following table for more info. These ROMs are responsible for sprite data. 

In addition to the four EPROMs, five bipolar PROMs will need to be replaced. Two are 82S123 and three are 82S129 (or equivalents). These are responsible for color outputs of background, sprite, and text tiles. If they are not replaced, the colors will be incorrect.

### Jumper Changes
Jumper J3 was set to open for Popeye. It should be set to **closed/on** for Sky Skipper.
