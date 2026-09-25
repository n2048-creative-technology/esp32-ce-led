# ESP32-C6 LED Controller Board

A compact 2-layer PCB built around the **ESP32-C6-WROOM-1** module, providing
USB-C power/programming, on-board 3.3V regulation, ESD-protected USB
data lines, a reset button, and an addressable/status LED header. All
electronic parts are sourced against JLCPCB's live parts catalog for
turnkey assembly.

## 3D Renders

| Top side (regulator / passives) | Bottom side (ESP32 module / USB-C) |
|---|---|
| ![PCB top 3D render](docs/images/pcb-3d-top.png) | ![PCB bottom 3D render](docs/images/pcb-3d-bottom.png) |

![PCB isometric 3D render](docs/images/pcb-3d-isometric.png)

## Schematic

![Schematic](docs/images/schematic.png)

Full-resolution vector version: [`docs/images/schematic.pdf`](docs/images/schematic.pdf)

## PCB Layout

![PCB layout](docs/images/pcb-layout.png)

*Copper (F.Cu / B.Cu), silkscreen, and solder mask layers, board outline shown.*

## Board Specs

- **Size:** 20.55 mm × 35.55 mm
- **Layers:** 2 (F.Cu / B.Cu)
- **MCU:** ESP32-C6-WROOM-1-N8 (Wi-Fi 6, Bluetooth 5 LE, Zigbee/Thread 802.15.4, 8 MB flash)
- **Power in:** USB-C (5V), on-board AMS1117-3.3 LDO regulator for 3.3V rail
- **USB protection:** USBLC6-2SC6-FS ESD protection on D+/D-
- **User I/O:** Reset button (SW1), status LED (D1), 2× 3-pin headers (J1/J2) for external LED/peripheral connections
- **ESD protection:** ESD9B3.3ST5G on EN line

## Bill of Materials

All parts verified against the live JLCPCB Open Platform API (real-time stock/pricing).
Full machine-readable BOM: [`BOM_jlcpcb_verified.csv`](BOM_jlcpcb_verified.csv)

| Ref | Part | LCSC # | Library |
|---|---|---|---|
| U1 | ESP32-C6-WROOM-1-N8 | C5366877 | Extended |
| U2 | USBLC6-2SC6-FS | C6807798 | Extended |
| U3 | AMS1117-3.3(TO-252) | C41347676 | Extended |
| D1 | KT-0603R (red LED) | C2286 | **Basic** |
| D4 | ESD9B3.3ST5G | C96512 | Extended |
| SW1 | B3U-1000P (tactile switch) | C231329 | Extended |
| J1, J2 | HX PH254-01-03-Z-L11.5 (1×3 header) | C52016391 | Extended |
| J4 | USB4105-GF-A (USB-C receptacle, 16P) | C3020560 | Extended |
| R1, R2 | 5.1kΩ 0402 | C25905 | **Basic** |
| R3 | 1kΩ 0402 | C11702 | **Basic** |
| R7, R8 | 10kΩ 0402 | C25744 | **Basic** |
| C1, C6 | 100nF 01005 | C307376 | Extended |
| C2, C3 | 22µF 0805 | C129302 | Extended |
| C4 | 1µF 0603 | C15849 | **Basic** |
| C5 | 10µF 0603 | C7472959 | Extended |

## Manufacturing

Board is set up for JLCPCB fabrication + assembly out of the box:

- Gerbers, drill files, pick-and-place, and BOM are already exported in this repo (`production/` and `*.gbr` / `*.drl` / `*-pos.csv` files)
- `esp32-c3-led.kicad_pro` / `.kicad_sch` / `.kicad_pcb` are the authoritative KiCad 9 source files
- Every part carries `LCSC` and `MPN` custom fields on its schematic symbol for direct BOM upload to JLCPCB

## Repo Layout

```
esp32-c3-led.kicad_pro      KiCad project
esp32-c3-led.kicad_sch      Schematic
esp32-c3-led.kicad_pcb      PCB layout
BOM_jlcpcb_verified.csv     Bill of materials with LCSC part numbers
docs/images/                Renders and diagrams (this README)
production/                 Fabrication outputs (gerbers, drill, pos files)
```
