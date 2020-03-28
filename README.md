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

#some detail about modbus CRC(CRC-16/MODBUS) algorithm quote from URL
http://modbus.org/docs/PI_MBUS_300.pdf
page 112-113
A procedure for generating a CRC is:
1. Load a 16–bit register with FFFF hex (all 1’s). Call this the CRC register.
2. Exclusive OR the first 8–bit byte of the message with the low–order byte
of the 16–bit CRC register, putting the result in the CRC register.
3. Shift the CRC register one bit to the right (toward the LSB), zero–filling the
MSB. Extract and examine the LSB.
4. (If the LSB was 0): Repeat Step 3 (another shift).
(If the LSB was 1): Exclusive OR the CRC register with the polynomial
value A001 hex (1010 0000 0000 0001).
5. Repeat Steps 3 and 4 until 8 shifts have been performed. When this is
done, a complete 8–bit byte will have been processed.
6. Repeat Steps 2 through 5 for the next 8–bit byte of the message.
Continue doing this until all bytes have been processed.
7. The final contents of the CRC register is the CRC value.
8. When the CRC is placed into the message, its upper and lower bytes
must be swapped as described below.


More crc catelogue  in 
http://reveng.sourceforge.net/crc-catalogue/16.htm

         name |       Check  | Poly  |  Init  |     RefIn |  RefOut |  XorOut
CRC-16/MODBUS |	0x4B37 |	0x8005 |	0xFFFF  |	true 	     | true 	  | 0x0000