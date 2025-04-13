# MicroMPPT

A compact 5W SPV1040-based MPPT (Maximum Power Point Tracking) solar charge controller designed with Meshtastic clients in mind.

## Overview

MicroMPPT is a small, efficient solar charging solution that utilizes the SPV1040T chip to implement a boost converter with Maximum Power Point Tracking. The design enables optimal energy harvest from solar panels by continuously adjusting the operating point to maximize power output under varying conditions.

- **Input**: Solar panel (up to 5W)
- **Output**: Configurable for different battery chemistries
- **Topology**: Boost converter with autonomous perturb-and-observe MPPT
- **Features**: Overvoltage protection, efficient energy harvest, compact design

## Block Diagram

```
┌─────────────┐    ┌───────────────┐    ┌────────────────────┐    ┌────────────────┐
│  Solar PV   │    │ OVP Circuit   │    │  MPPT Controller   │    │                │
│  Input      │───►│ (PMOS + Zener)│───►│  (SPV1040T)        │───►│  Battery Load  │
│             │    │               │    │  - Boost Converter │    │                │
└─────────────┘    └───────────────┘    │  - P&O Algorithm   │    └────────────────┘
                                        └────────────────────┘
                                                 │
                                        ┌────────▼─────────┐
                                        │  Sensing Circuit │
                                        │  - Current Sense │
                                        │  - Voltage Div   │
                                        └──────────────────┘
```


## Project Structure

| Path | Description |
|------|-------------|
| `/elec/src/micromppt.ato` | Main circuit definition file using the Atopile language |
| `/elec/src/SPV1040T.ato` | SPV1040T component definition |
| `/elec/layout/default/micromppt.kicad_pcb` | KiCad PCB layout file |
| `/build/builds/default` | Generated build outputs (Gerbers, BOM, 3D models) |

## Key Features

- **Autonomous MPPT**: Self-adjusting maximum power point tracking using the perturb-and-observe algorithm
- **Multi-chemistry Support**: Configurable for different battery types
- **Compact Design**: Small form factor for embedded applications
- **Overvoltage Protection**: Prevents damage from excessive input voltage
- **High Efficiency**: Optimizes energy transfer from solar panels

## Circuit Operation

1. **Input Stage**: Solar panel connects to the input with overvoltage protection
2. **MPPT Control**: SPV1040T continuously adjusts the operating point to maximize power
3. **Boost Conversion**: Steps up input voltage as needed for battery charging
4. **Output Stage**: Regulated output for charging batteries or supercapacitors

## Documentation and Links

- [Project Website](https://eigenlucy.github.io/projects/micromppt/)
- [Hackaday Project Page](https://hackaday.io/project/202610-micromppt)
- [SPV1040 Datasheet](https://www.st.com/resource/en/datasheet/spv1040.pdf)

## Built With Atopile

This project is built using [Atopile](https://atopile.io/).

Check out [ATO_USAGE.md](ATO_USAGE.md)

## License

This project is licensed under the MIT License - see the LICENSE file for details.
