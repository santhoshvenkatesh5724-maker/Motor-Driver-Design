# Changelog

## [V1.0] — unreleased

First public design.

- STM32G474 + DRV8323RS FOC drive, 6 × BSC019N06NS, 3 × 1 mΩ low-side shunts
- EtherCAT (LAN9253, 2 ports), CAN FD (TCAN1044V) with ESD protection; CAN termination via jumper on the output connector
- ASM330LHHX IMU on the shared I2C bus with the EEPROM
- DRV8251 brake output
- Reverse-polarity PFET removed (use keyed connector + inline fuse)
