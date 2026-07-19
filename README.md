# Dakboard HDMI Dimmer - Hardware

A Raspberry Pi HAT that carries a BH1750 ambient-light sensor and a PIR motion sensor for automatic HDMI display dimming.

Designed for the Raspberry Pi Zero 2 W, but it mounts on any Raspberry Pi with the standard 40-pin header. Pairs with [Dakboard-HDMI-dimmer-FW](https://github.com/DotaPie/Dakboard-HDMI-dimmer-FW), which reads these sensors and adjusts display brightness.

## What's on the board

- **40-pin GPIO header (J1)** - mounts the board as a HAT and breaks out power, I²C, and the PIR line
- **BH1750 light sensor header (J2)** - 5-pin module (VCC / GND / SCL / SDA / ADDR) on I²C bus 1, address `0x23`, with 4K7 pull-ups
- **PIR motion sensor header (J3)** - 3-pin module (VCC / OUT / GND) with the output on GPIO24 (BCM), physical pin 18
- Decoupling and signal-conditioning passives, plus four mounting holes

The BH1750 runs at 3.3 V on the Pi's primary I²C bus; the PIR is powered from 5 V and its output is fed to a GPIO. All dimming logic lives in the firmware - this board just carries the sensors.

## Pin usage

| Signal   | Raspberry Pi pin        | Notes                        |
|----------|-------------------------|------------------------------|
| I²C SDA  | GPIO2 / pin 3           | BH1750 (bus 1, addr `0x23`)  |
| I²C SCL  | GPIO3 / pin 5           | BH1750                       |
| PIR out  | GPIO24 / pin 18         | Motion detection             |
| 3V3      | pin 1                   | BH1750 supply                |
| 5V       | pin 2 / pin 4           | PIR supply                   |
| GND      | pins 6, 9, 14, …        | Common ground                |

## Board specs

- Size: **30 × 65 mm**
- 4× mounting holes
- 2-layer, JLCPCB-ready gerbers included

## Repository layout

```
Dakboard HDMI dimmer KiCAD/
└─ Dakboard HDMI dimmer v1/
   ├─ Dakboard HDMI dimmer v1.kicad_pro   # KiCAD project
   ├─ Dakboard HDMI dimmer v1.kicad_sch   # schematic
   ├─ Dakboard HDMI dimmer v1.kicad_pcb   # PCB layout
   └─ gerber_to_order/                    # zipped gerbers for JLCPCB
```

## Manufacturing

The gerber archive in `gerber_to_order/` is ready to upload to [JLCPCB](https://jlcpcb.com/) (or any fabricator) as-is. To modify the design, open the project in [KiCAD](https://www.kicad.org/) 7 or newer.

## Below is an example of full HW installation with custom cabling

<img width="545" height="907" alt="Snímka obrazovky 2026-07-19 014746" src="https://github.com/user-attachments/assets/53bc5359-ebfc-4817-b979-dbe4fa9f4b6a" />
<img width="3000" height="4000" alt="20260607_161944" src="https://github.com/user-attachments/assets/bf986c6a-06da-4745-a4c8-6066a58a8712" />
<img width="3000" height="4000" alt="20260607_170730" src="https://github.com/user-attachments/assets/729144fb-1ba8-4100-a02a-4949af2f7abd" />
<img width="3000" height="4000" alt="20260607_172544" src="https://github.com/user-attachments/assets/96e8d1f2-ef64-48d8-98fa-cdc495262558" />
<img width="3000" height="4000" alt="20260607_173511" src="https://github.com/user-attachments/assets/f1c963a1-4b0e-49d9-b4f6-58f8fe9583f3" />

