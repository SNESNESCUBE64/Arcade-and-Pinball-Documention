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
- small flathead screwdriver or chip lifter
- programmer capable of burning required ROM ICs

## CPU PCB (TNX1-0*-CPU)
### ROM Replacement
There are eight 2732 EPROMs populated from 2A to 2H. These will need to be replaced with the seven Sky Skipper ROMs. Refer to the following table for more ROM info.

**Note: 2H is left unpopulated on Sky Skipper**

| **Filename** | **ROM Location** | **ROM Type** | **ROM Size** | **CRC32** |
|--------------|:----------------:|:------------:|:------------:|:---------:|
| tnx1-c.2a    |        2A        |     2732     |      4k      |  BDC7F218 |
| tnx1-c.2b    |        2B        |     2732     |      4k      |  CBE601A8 |
| tnx1-c.2c    |        2C        |     2732     |      4k      |  5CA79ABF |
| tnx1-c.2d    |        2D        |     2732     |      4k      |  6B7A7071 |
| tnx1-c.2e    |        2E        |     2732     |      4k      |  6B0C0525 |
| tnx1-c.2f    |        2F        |     2732     |      4k      |  D1712424 |
| tnx1-c.2g    |        2G        |     2732     |      4k      |  8B33C4CF |

### Jumper Changes
Jumper J9 was set to closed for Popeye. It should be changed to **open/off** for Sky Skipper.

## Video PCB (TNX1-0*-VIDEO)
### ROM Replacement
There is one 2716 eprom on the video PCB. This will need to be replaced with the Sky Skipper ROM. 

| **Filename** | **ROM Location** | **ROM Type** | **ROM Size** | **CRC32** |
|--------------|:----------------:|:------------:|:------------:|:---------:|
| tnx1-v.3h    |        3H        |     2716     |      2k      |  ECB6A046 |

## Tile Interface PCB (TNX1-0*-TIF)
### ROM Replacement
There are two daughterboards placed in the EPROM sockets on the TIF board. These will need to be removed along with the extra wire. Be aware that daughterboards are in there tight. It is encouraged to replace these sockets as 40+ years of oversized pins likely pushed the socket pins in too far to make proper EPROM connection.

In place of the daughterboards will be four **2532** EPROMs. Note that 2732 EPROMs will not work without board modifications, use 2532 instead. Refer to the following table for more info. These ROMs are responsible for sprite data. 

In addition to the four EPROMs, five bipolar PROMs will need to be replaced. Two are 82S123 and three are 82S129 (or equivalents). These are responsible for color outputs of background, sprite, and text tiles. If they are not replaced, the colors will be incorrect.

| **Filename** | **ROM Location** | **ROM Type** | **ROM Size** | **CRC32** |
|--------------|:----------------:|:------------:|:------------:|:---------:|
| tnx1-t.1e    |        1E        |     2532     |      4k      |  01C1120E |
| tnx1-t.2e    |        2E        |     2532     |      4k      |  70292A71 |
| tnx1-t.3e    |        3E        |     2532     |      4k      |  92B6A0E8 |
| tnx1-t.5e    |        5E        |     2532     |      4k      |  CC5F0AC3 |
| tnx1-t.1a    |        1A        |    82S123    |      32      |  C2BCA435 |
| tnx1-t.2a    |        2A        |    82S129    |    256 x 4   |  AA7FF322 |
| tnx1-t.3a    |        3A        |    82S129    |    256 x 4   |  8ABF9DE4 |
| tnx1-t.4a    |        4A        |    82S123    |      32      |  98846924 |
| tnx1-t.3j    |        3J        |    82S129    |    256 x 4   |  1C5C8DEA |


### Jumper Changes
Jumper J3 was set to open for Popeye. It should be set to **closed/on** for Sky Skipper.

### Populate Resistor at R25
A 3.3k ohm resistor must be added to R25. It is unpopulated on Popeye converted PCB.

