# Zorrology
Dumb dual clock port for the Amiga Zorro II expansion bus.

<img src="https://github.com/andersmilton/zorrology/blob/main/images/Zorrology%20line%20drawing.png" alt="Zorrology line drawing" />

## About
<img src="https://github.com/andersmilton/zorrology/blob/main/images/Zorrology%20Rev%201%20front.jpg" alt="Zorrology Rev 1 front" width="33%" align="right" />
<img src="https://github.com/andersmilton/zorrology/blob/main/images/Zorrology%20Rev%201%20back.jpg" alt="Zorrology Rev 1 back" width="33%" align="right"/>
Zorrology is an expansion for the Amiga Zorro II expansion bus, providing two clock ports. The clock port is an expansion port originally only found in the Amiga 1200, and originally mainly meant to be used for a realtime clock, but as useful expansions has been developed, these kinds of ports has been added to various other Amiga models. Be aware that a realtime clock cannot be added to an Amiga using the clockports provided by Zorrology. Isn’t it ironic, don’t you think?

## Hardware configuration
The default address for Clockport 1 of Zorrology is 0xEE0001, and for Clockport 2 0xEE4001. The base address is configured by DIP switches on the card itself, and cannot be configured in software. Clockport 1 is located one byte above the base address and Clockport 2 is always located at 0x4000 above Clockport 1. If you are experiencing problems such as bus congestions, the base address can be reconfigured, either according to the table provided on the GitHub project page, or calculated if you are comfortable converting between binary and hexadecimal.

## Hardware installation
Install Zorrology in a free Zorro II slot, making sure that the FRONT arrow on the card is facing the front of your Amiga. For details on how to install expansion cards in your Amiga, please refer to the documentation for your Amiga.

After installing Zorrology in your Amiga, fit your clock port expansion(s) on Zorrology on the headers marked “Clockport 1” and/or “Clockport 2”. 

**MAKE SURE THAT THE CLOCK PORT EXPANSION IS FACING THE RIGHT WAY!**

The clock ports on Zorrology are facing the same way as they are on an Amiga 1200; if the expansion is made to face to the back of an Amiga 1200, it should be facing the same way on Zorrology. For example images, see the Zorrology GitHub project page.

## Software configuration
As Zorrology is a “dumb” expansion, i e doesn’t do autoconfiguration for obtaining an address, sometimes the user will have to manually configure the Amiga software to let the address range configured by the DIP switches on Zorrology be used.

If you have a 68040 or 68060 CPU you will most likely have a MMU that's configured to only allow access to Zorro cards that are autoconfigured. This might also be the case if you have a 68030, but it depends on your setup. If you run into trouble because of your MMU you can try the following lines in your shell or S:User-Startup, making sure to change the address given in the commands above if you are using another base address than the default:

```
MuSetCacheMode 0xEE0000 0x10000 INVALID	
MuSetCacheMode 0xEE0000 0x10000 CACHEINHIBIT IOSPACE VALID
```

Most clock port expansions are by default configured to use the address 0xD80001. Please refer to the documentation for your clock port expansion on how to change this to the address used by Zorrology Clockport 1 or Clockport 2, depending on which port is used.

