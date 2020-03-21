# CRC releated information

#OverView

Introduce to the algorithm and  details about Check Poly Init RefIn RefOut XorOut

# How to Check 

1. Separate the message and checksum.
2. Check the whole data and see if it comes out as zero!

# Check
 a check value on the nine-byte string of ASCII digits "123456789"
# Poly
Value of the poly
# Init
Initial value for the register

#RefIn
This is a boolean parameter. If it is FALSE, input bytes are
   processed with bit 7 being treated as the most significant bit
   (MSB) and bit 0 being treated as the least significant bit. If this
   parameter is FALSE, each byte is reflected before being processed.
#RefOut
This is a boolean parameter. If it is set to FALSE, the
   final value in the register is fed into the XOROUT stage directly,
   otherwise, if this parameter is TRUE, the final register value is
   reflected first.
#XorOut
This is an W-bit value that should be specified as a
   hexadecimal number. It is XORed to the final register value (after
   the REFOUT) stage before the value is returned as the official
   checksum







                 Check   Poly   Init     RefIn  RefOut   XorOut
CRC-16/MODBUS 	0x4B37 	0x8005 	0xFFFF 	true 	true 	0x0000