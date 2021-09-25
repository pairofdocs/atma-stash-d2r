# Atma Stash to D2R Converter
Drag and drop your `.d2x` Atma stash file to convert it to a `.d2i` D2R stash.  
https://pairofdocs.github.io/atma-stash-d2r/


## Original Converter
All credit goes to Riv for his D2 <--> D2R converter.  
Code was used from https://github.com/d07RiV/d07riv.github.io


## Stash File Formats
[Table](https://github.com/squeek502/d2itemreader/blob/master/docs/formats/atma.md) from https://squeek502.github.io/d2itemreader/formats/atma.html

### ATMA Stash (.d2x) File Format

ATMA is the file format used by the [ATMA](http://atma.incgamers.com/) and [GoMule](http://gomule.sourceforge.net/) muling tools.

Byte Offset | Size (bytes) | Description
------------|:------------:|-------------
0x00 | 3 | File header. Must be "D2X".
0x03 | 2 | Number of items in the file as a 16 bit unsigned integer.
0x05 | 2 | File version as a 16 bit unsigned integer. Must be 96.
0x07 | 4 | ATMA checksum. See [here](https://github.com/sylecn/gomule/blob/27731580051afc7e171996997231e42a9f17cd6f/src/gomule/d2x/D2Stash.java#L176-L199) for how this is calculated.
0x0B | ... | Beginning of [D2 Item List data](d2.html#item-list-data-format) *without* the 'header' and 'number of items' fields. Instead, use the value at offset 0x03 of the ATMA data as the number of 'root' items in the list, and then read the item list as if you're starting at offset 0x04 of the item list data.
