# The specification for SPXI (or how I did it)
This will be updates as features are added or deprecated (backwards compatabilty is not a focus at current). 

# The Header
Where all the important information about how to interprete the information will reside

### A note about bit significance
I'm simple, so I use right-aligned least significant bit (LSB) and so will this

## Magic Number
#### Byte Footprint: 4
The magic number is a check to make sure that the generated or target file is actually one attempting to follow the SPXI format within this doc.  

The number is encoded in standard ASCII characters, 4 of them to be exact, spelling out "SPXI" (this is case sensitive).  
| Encoding | Sequence |  
| -------- | -------- |  
| ASCII    | SPXI     |  
| Hex      | 0x53 0x50 0x58 0x49 |

## Version
#### Byte Footprint: 2
I've been told by many a code guru that versioning is important, so here it is. Two bytes shouldn't ever not be enough.

## Bits Per Pixel
#### Byte Footprint: 1
How many bits each pixel entry in the data section of the file gets. Note unused bits in a byte should be considered filler (zero'ed out).  
| BPP | Supported |  
| --- | --------- |  
| 8   | No        |  
| 16  | No        |  
| 24  | Yes       |  
| 32  | No        |  
As of this commit I only intend adding transparency to 32 BPP.

## Header Size
#### Byte Footprint: 1
How many bytes the header is going to occupy (magic number and version inclusive).

## Color Bitmasks
#### Byte Footprint: 1 - 4 (Check BPP)
As of this commit only 24 BPP is supported to get the project off the ground, as so the bitmask is rather simple.  
8 bits for red, 8 bits for green, and 8 bits for blue, in that order.

## Image Dimensions
#### Byte Footprint: 4 x 2
For both the height and width 4 bytes (64 bit) are allocated for each (summating to 8 bytes). First section is the height, second section is the width.

# The Pixel Data
As of this commit, the data is raw, so there is no compression at work, read as provided. The data is stored top-left to bottom-right.