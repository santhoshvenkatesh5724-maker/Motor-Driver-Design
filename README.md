# Motor Driver V1 — open-source FOC servo drive for robotic arm joints

A 4-layer field-oriented-control (FOC) motor driver built for the LA8308 outrunner
(36N40P, KV90) in a 10 kg-payload robotic arm, with EtherCAT and CAN FD on board.

> **Status: V1.0 — designed, not yet fabricated or bench-validated.** Expect errata.

## Key specs

| | |
|---|---|
| Bus voltage | 20–30 V (8S LFP, 24 V nominal) |
| Phase current | 15 A RMS sustained, 25 A peak (design target) |
| MCU | STM32G474MET6 (LQFP80, 170 MHz Cortex-M4F) |
| Gate driver | TI DRV8323RS (SPI, 3 integrated CSAs) |
| Power stage | 6 × Infineon BSC019N06NS (60 V, 1.9 mΩ), 3 × 1 mΩ low-side shunts |
| Fieldbus | EtherCAT (Microchip LAN9253, 2 ports) + CAN FD (TI TCAN1044V) |
| Sensors | Encoder connector (SPI + ABZ, e.g. MT6835), ASM330LHHX 6-axis IMU, NTC |
| Brake output | TI DRV8251, single-ended high-side for a spring-applied brake solenoid |
| PCB | 100 × 60 mm, 4 layers (2 oz outer / 1 oz inner), blind vias L1–L2 and L3–L4 |
| EDA | EasyEDA Pro |

## ⚠️ No reverse-polarity protection

This board has **no on-board reverse-polarity protection**. A reversed supply forward-biases
the MOSFET body diodes and the input TVS and will destroy the board. Use a keyed connector
(XT90) and an inline fuse (~30 A) in the battery lead; with a reversed connection the TVS then
crowbars the supply and blows the fuse.

## Repository layout

```
hardware/
  easyeda/      EasyEDA Pro project source (.eprj / exported .epro)
  schematic/    Schematic PDF
  fab/gerbers/  Gerbers + drill files, as sent to the fab
  fab/bom/      BOM and pick-and-place
docs/           Design notes, bring-up notes, images
```

## Building one

1. Order the PCB from `hardware/fab/gerbers/` (4-layer, 1.6 mm, 2 oz outer / 1 oz inner,
   blind vias L1–L2 and L3–L4, ENIG recommended).
2. Assemble from `hardware/fab/bom/`.
3. First power-up on a current-limited bench supply (≤ 0.5 A) with the motor disconnected.

## Licences

| Part | Licence |
|---|---|
| Hardware design (everything in `hardware/`) | [CERN-OHL-S v2](LICENSE) |
| Documentation (`docs/`, this README) | [CC BY-SA 4.0](LICENSE-docs) |

If you modify and distribute this hardware (including selling boards), you must publish
your modified design source under the same licence. See [LICENSE](LICENSE).

Source location: https://github.com/santhoshvenkatesh5724-maker/Motor-Driver-Design

## Contributing

Issues and pull requests welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

Copyright © 2026 Santhosh
