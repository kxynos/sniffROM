# sniffROM
A tool for passive data capture and reconnaissance of serial flash chips. It is used in conjunction with a Saleae logic analyzer to reconstruct flash memory contents and extract contextual information about device operations.

* Supports <b>SPI</b> and <b>I²C</b> flash chips.
* Preserves the actual memory addresses of captured data.
* Generates a <b>visual map</b> of the reconstructed binary image.
* Generates a <b>timing plot</b> of reads/writes to memory addresses. 
* Recognizes <b>100+</b> (and currently parses <b>12</b>) SPI flash commands from the following manufacturers:
  * Atmel
  * Eon
  * Fidelix
  * GigaDevice
  * Macronix
  * Numonyx 
  * Spansion
  * SST
  * Winbond

See the [Wiki](https://github.com/alainiamburg/sniffROM/wiki) for documentation
```
usage: sniffROM.py [-h] [--addrlen [{2,3,4}]] [--endian [{msb,lsb}]]
                   [--filter [{rw,r,w,no_regs}]] [-o [O]] [--summary]
                   [--data-map] [--timing-plot] [-v] [--correct-id]
                   input_file

sniffROM - Reconstructs flash memory contents and extracts other data from
passively sniffed commands in a Saleae logic analyzer capture file. Currently
supports SPI and I2C flash chips.

positional arguments:
  input_file            Saleae Logic SPI or I2C Analyzer Export File (.csv)

optional arguments:
  -h, --help            show this help message and exit
  --addrlen [{2,3,4}]   set length of SPI memory address in bytes (default: 3)
  --endian [{msb,lsb}]  set endianness of SPI memory bytes (default: msb)
  --filter [{rw,r,w,no_regs}]
                        analyze only Read or Write commands (default: both),
                        no_regs filters out Status Register output
  -o [O]                flash image output file name (default: output.bin)
  --summary             print summary of sniffed commands and metadata
  --data-map            show visual data map
  --timing-plot         show timing analysis
  -v                    increase verbosity (up to -vvv)
  --correct-id          attempt to correct the packet id based on a READ
                        command (end might be incorrect)
```
