# One-Handed Keyboard

> We received a special email. The sender's daughter lost the use of her right hand permanently after being run over by a heavy truck on her way to school. When using a computer, she has to frequently switch between the keyboard and mouse [...]

![Left-Hand Small Keyboard](/Docs/Image/左手小键盘右侧面.jpg "Left-Hand Small Keyboard")

![Left-Hand Large Keyboard](/Docs/Image/左手大键盘右侧.jpg "Left-Hand Large Keyboard")

This is a single-mode mechanical keyboard with an integrated trackball. The firmware uses [QMK](https://github.com/qmk/qmk_firmware). Thanks to all developers who contributed to the QMK community.

Keyboard design referenced: [【He Tongxue】We made a special keyboard…](https://www.bilibili.com/video/BV1DtjAzUEb9)

Hardware open source: [HTXStudio One-Handed Keyboard](https://oshwhub.com/htx-studio/One-Handed_Keyboard)

[GitHub repository](https://github.com/htx-studio/One-Handed-Keyboard)

[Gitee repository](https://gitee.com/htxstudio/one-handed-keyboard)

Reference [here](https://docs.qmk.fm/newbs_getting_started "Set up your QMK environment") for development environment and setup. Firmware source code is [here](https://github.com/htx-studio/qmk_firmware/tree/master/keyboards/htx_st...).

Contents of this repository include:

* 8 PCB designs for three types of keyboards (left and right hand), provided as Lichuang EDA projects.
* VIA key remapping configuration files and pre-compiled firmware.
* Model design files.

---

## Repository Directory Structure

#### Docs (Documentation)

Chip datasheets and images.

#### Firmware

QMK firmware for three different keyboard models, as well as the JSON files for key remapping via VIA.

#### Hardware

JLCPCB EDA project files.

#### Model

Model and machining files for each keyboard model.

---

## Production Guide

### PCB:

1-Right-Hand Keyboard - Hot-Swap (Large): FR-4, 1.6mm thick, 4-layer board, JLC04161H-3313 stackup, impedance control +/-20%.

1-Left-Hand Keyboard - Soldered (Small): FR-4, 1.6mm thick, 2-layer board. ALPS yellow switches require firm insertion during installation.

1-Left-Hand Keyboard - Hot-Swap (Large): FR-4, 1.6mm thick, 4-layer board, JLC04161H-3313 stackup, impedance control +/-20%.

2-TypeC: FR-4, 1.6mm thick, 2-layer board, labeled CON1 (for large keyboard only).

3-Trackball: FR-4, 1.6mm thick, 2-layer board. Pay attention to soldering orientation, labeled CON3.

4-Mouse Wheel: FR-4, 1.6mm thick, 2-layer board. Recommend 7mm high encoder, 6mm high switches, switch actuation force ≤180g, labeled CON2.

5-Directional Keys: FR-4, 1.6mm thick, 2-layer board. ALPS yellow switches require firm insertion during installation, labeled CON4.

6-Main Control Board - Left Hand (Small): FR-4, 1.6mm thick, 2-layer board.

> * Three models share the same small control boards: `3-Trackball`, `4-Mouse Wheel`, `5-Directional Keys`.
> * `5-Directional Keys` and `1-Left-Hand Keyboard - Soldered (Small)` use ALPS yellow switches.
> * Note: Large keyboards for left and right hands are not completely mirrored.
> * Trackball uses SPI1 channel for control; the wheel has two separate signal lines—this allows replacing other control devices with minimal adjustment.
> * Main controller: STM32G431CBU6.
> * Compatible with A to C or C to C data cables.

### Printed Parts:

Keycaps: Resin, PLA, etc.

Trackball Holder: Resin, PLA, etc.

Mouse Buttons: Resin, PLA, etc.

Case: Resin, PLA, etc.

Base: Resin, PLA, etc.

### Machining:

Positioning Plate: Recommended material—POM, thickness 1.5mm.

Positioning Plate Cotton Strip: One side adhesive.

Sandwich Cotton: Recommended material—Poron, thickness 3.5mm.

Switch Mount Cotton: Thickness 2mm.

Bottom Cotton: Recommended material—Poron, thickness 4mm.

Silicone Pad (small keyboard only): Thickness 5mm, hardness Shore 00-10.

### Hardware:

|                    | Large Keyboard Qty | Small Keyboard Qty |
| :----------------- | :----------------: | :----------------: |
| M3×3×4 Hot Melt Brass Nut |      8       |        8           |
| M2×2×3 Hot Melt Brass Nut |      2       |        -           |
| M2×3×3 Hot Melt Brass Nut |     17       |       12           |
| M3×6 Countersunk Screw    |      2       |        6           |
| M3×15 Countersunk Screw   |      -       |        4           |
| M3×22 Countersunk Screw   |      6       |        -           |
| M2×8 Socket Head Screw    |      4       |        4           |
| M2×3 Socket Head Screw    |      2       |        -           |
| M2×5 Socket Head Screw    |     13       |        8           |
| M3×16 Flat Head Screw     |      -       |        2           |

### Others:

Trackball: 25mm diameter, PTFE material.

Lubrication Balls: 2mm diameter, PTFE material, installed in the 3D printed trackball holder, 6 in total.

Scroll Wheel: Recommended diameter 19–20mm, thickness 4–5mm, metal.

Stabilizer: 2U steel plate stabilizer.

Switches: 57 ultra-small ALPS yellow switches for small keyboard, 57 standard mechanical switches for large keyboard.

Ribbon Cable: 0.5mm pitch, 8P reverse, two 10cm, two 15cm.

> * All FPC connectors on control and small boards are labeled CON and correspond to their matching interfaces.
> * The files use FPC connectors that can be connected from both sides. When all connectors are connected from below, use reverse ribbon cables.

### Model Structure:

![Left-Hand Small Keyboard Exploded](/Docs/Image/左手小键盘爆炸图.jpg "Left-Hand Small Keyboard Exploded")

![Left-Hand Large Keyboard Exploded](/Docs/Image/左手大键盘爆炸图.jpg "Left-Hand Large Keyboard Exploded")

### Assembly Sequence:

> Taking the large keyboard as an example

**Pre-assembly Preparation**

* First, connect the four small PCBs to the main keyboard PCB with ribbon cables and flash the firmware.
* Install 3–5 switches, the scroll wheel, and the trackball. Make sure they function properly before assembly.
* Install the correct hot melt brass nuts in the corresponding positions on the 3D printed case and base.
* Print legends on keycaps.
* Stick cotton strips to the raised parts of the positioning plate (on both sides).

> For the first firmware flash, press the button labeled "B" on the back of the PCB and then insert the USB cable.
>
> To update the firmware later, hold the "ESC" key on the keyboard and insert the USB cable.
>
> For more details, refer to [Flashing Your Keyboard (QMK)](https://docs.qmk.fm/newbs_flashing)

**Start Assembly**

1. Use screws to install the four small boards into their positions on the base (note ribbon cable orientation); the trackball holder is screwed in from below.
2. Fix the left and right mouse buttons to the keyboard PCB with screws.
3. From bottom to top, place the bottom cotton, switch mount cotton, keyboard PCB, sandwich cotton, and positioning plate into the fan-shaped section of the base in order.
4. Insert the switches.
5. Put on the case and secure it from below with screws.
6. Install keycaps to complete assembly.

> For a screw and nut installation guide, refer to [here](https://github.com/htx-studio/One-Handed-Keyboard/tree/main/Model)

Finally, this is our first open-source project. If there are any shortcomings, we welcome your criticism and suggestions. Thank you all!

---

## References

[Quantum Mechanical Keyboard Firmware](https://docs.qmk.fm/)

mrjohnk. ADNS-9800. [GitHub repository](https://github.com/mrjohnk/ADNS-9800/)

---