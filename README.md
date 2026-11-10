# 6gend-hvst-db-1

Dual-Source Energy Harvesting Daughter Board for the END Platform

Part of the **AMBIENT-6G Energy Neutral Device (END) Platform**:
https://github.com/AMBIENT-6G/END-Platform

## Overview

The **6gend-hvst-db-1** is a dual-source energy harvesting daughter board for the END Platform based on the **e-peas AEM13921** energy harvesting PMIC. The board is intended as a research platform for investigating hybrid energy harvesting systems that combine **RF energy harvesting** with a second ambient energy source such as photovoltaic, thermal, vibration, or other DC energy harvesters.

The AEM13921 integrates two independent harvesting inputs, each featuring configurable Maximum Power Point Tracking (MPPT) or constant-voltage regulation. Harvested energy is stored in an external rechargeable storage element and supplied to the application through an integrated high-efficiency buck converter.

The board interfaces with an END Platform main board through the standard 12-pin END Platform connector and provides monitoring and configuration capabilities through an I²C interface.

## Features

- e-peas **AEM13921** dual-source energy harvesting PMIC
- Two independent energy harvesting inputs
- Simultaneous harvesting from both sources
- MPPT operation on both harvesting inputs
- Constant-voltage harvesting mode support
- Dedicated **5 V charging input**
- Integrated storage management
- Support for:
  - Supercapacitors
  - Lithium-Ion Capacitors (LiC)
  - Li-Ion batteries
  - LiPo batteries
- Integrated overcharge protection
- Integrated overdischarge protection
- Temperature monitoring of the storage element
- Configurable safety thresholds
- Average Power Monitoring (APM) through I²C
- Integrated high-efficiency buck converter
- Dynamic configuration through I²C
- Hardware configuration through solder-selectable GPIO settings
- Cold start from as low as **275 mV / 1.5 µW**
- Harvesting operation down to **120 mV after startup**
- END Platform compatible connector interface

## Board Image

[Picture of the PCB design in KiCAD](6gend-hvst-db-1.png)

## Purpose

The primary purpose of this board is to support research into:

- Hybrid energy harvesting systems
- RF energy harvesting
- Multi-source energy management
- Energy-neutral IoT systems
- Ambient energy harvesting optimization
- Storage technology evaluation
- Power-aware embedded systems
- Ultra-low-power wireless sensor nodes
- Energy availability monitoring and prediction

Typical applications combine an RF harvesting source with a second energy source such as:

- Solar cells
- Thermoelectric generators (TEGs)
- Piezoelectric harvesters
- Vibration harvesters
- Pulsed energy sources
- Other low-power DC sources

## Hardware Architecture

### AEM13921 Energy Harvesting PMIC

The board is built around the **e-peas AEM13921**, an ultra-efficient dual-source energy harvesting power management IC.

Key capabilities include:

- Two independent boost converters
- Independent MPPT configuration for each source
- Constant-voltage source regulation
- Simultaneous harvesting from both inputs
- Integrated storage charging and protection
- Integrated buck converter output
- Energy flow monitoring through Average Power Monitoring (APM)

The device can determine how much energy has been transferred from each harvesting source and from the 5 V charger into the storage element, as well as the energy delivered from storage to the load through its APM functionality.

### Energy Harvesting Inputs

The AEM13921 supports two harvesting channels.

Each input can be independently configured for:

- Open-circuit voltage ratio MPPT
- Constant-voltage regulation

This makes it possible to optimize energy extraction from a broad range of harvesting technologies while simultaneously harvesting from both sources.

A common use case is:

- Source 1: RF energy harvester
- Source 2: Solar cell

but other combinations are equally possible.

### 5 V Charging Input

In addition to the harvesting inputs, the board provides a dedicated **5 V charging input**.

This interface allows:

- Rapid charging of the storage element
- Recovery from depleted storage conditions
- Laboratory testing and characterization
- Development without requiring ambient energy sources

### Storage Management

The board supports a wide variety of rechargeable storage technologies including:

- Supercapacitors
- Lithium-Ion Capacitors (LiC)
- Lithium-Ion batteries
- Lithium-Polymer batteries

The AEM13921 provides configurable:

- Charge-ready thresholds
- Overcharge protection
- Overdischarge protection

These protection mechanisms increase storage lifetime and ensure safe operation.

### Thermal Monitoring

A dedicated temperature monitoring circuit is provided for the storage element.

This functionality allows:

- Monitoring storage temperature through the PMIC
- Over-temperature protection
- Under-temperature protection
- Safe charging and discharging operation

Temperature protection can be configured independently for charge and discharge conditions.

### Buck Converter Output

The harvested and stored energy is delivered to the application through the integrated high-efficiency buck converter.

Features include:

- Output voltage configurable between 0.6 V and 3.3 V
- High conversion efficiency
- Output current capability up to 100 mA

This allows efficient powering of ultra-low-power sensors, microcontrollers, and wireless communication systems.

### Configuration Interface

The board supports two configuration methods:

#### GPIO Configuration

The AEM13921 configuration pins can be statically configured using solder bridges on the PCB.

Depending on the solder bridge population, configuration pins may be tied:

- High
- Low

This allows standalone operation without software configuration.

#### I²C Configuration

All important system parameters can also be configured dynamically through I²C.

Available functionality includes:

- Reading system status
- Monitoring energy flow information
- Modifying PMIC operating parameters
- Reconfiguring protection thresholds
- Harvesting optimization

## Connector Pinout

The board follows the END Platform harvesting connector definition.

| Pin | Function |
|------|----------|
| 1 | NC |
| 2 | IRQ |
| 3 | SCL |
| 4 | SDA |
| 5 | GND |
| 6 | VCC |
| 7 | ST_LOAD |
| 8 | ST_STO |
| 9 | NC |
| 10 | NC |
| 11 | GND |
| 12 | VBAT |

## MCU Interface

Communication with the host controller is performed through **I²C**.

Required signals:

- SCL
- SDA
- IRQ

The host MCU can use the I²C interface to:

- Configure harvester settings
- Read energy monitoring information
- Read system status
- Monitor storage conditions
- Access thermal protection status

## Design Status

**Status: Under Debug**

The hardware has been:

- Designed
- Manufactured
- Assembled

Current activities:

- Hardware validation
- Firmware development
- Functional debugging
- System characterization

The board is operational but still undergoing verification and debugging.

## License

### CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S-2.0)

This project is released under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal**.

You may:

- Study the design
- Modify the design
- Manufacture the design
- Distribute the design

provided that derivative hardware designs remain available under the same license.

A copy of the license can be obtained from:

https://cern-ohl.web.cern.ch/

## Citation

If you use this design in academic work, please cite:

6gend-hvst-db-1: Dual-Source Energy Harvesting Daughter Board for the END Platform,
DRAMCO Research Group, KU Leuven.

## Contact

**DRAMCO Research Group**  
KU Leuven – Ghent Campus  
Gebroeders De Smetstraat 1  
9000 Ghent  
Belgium

END Platform Repository:
https://github.com/AMBIENT-6G/END-Platform