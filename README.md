**# Arnoll Rhythmboard 1

An easily customizable controller for most computer rhythm games.

Suitable for multiple games, including:

| | | | |
| - | - | - | - |
| osu! | DJMAX RESPECT V | Quaver | vivid/stasis |
| Milthm | Rhythm Doctor | Sparebeat | Polylylyrhythm |
| Estella | In Falsus (theoretically) | etc. | |

The overall layout and default keymap are optimized for DJMAX RESPECT V, but any games similar to this are supported. You only need to edit the keymap in [ZMK Studio](https://zmk.studio/) to easily optimize the Rhythmboard for the game you're playing or your preferred key bindings.

<!-- TODO: Images and photos -->

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Get Started](#get-started)
  - [Install Firmware](#install-firmware)
  - [Build from hardware](#build-from-hardware)
    - [BOM](#bom)
    - [1. Prepare and Print PCB](#1-prepare-and-print-pcb)
    - [2. Solder Everything](#2-solder-everything)
    - [3. Assembly](#3-assembly)
    - [4. Install Firmware](#4-install-firmware)
- [Default keymap](#default-keymap)
  - [Customize your keymap](#customize-your-keymap)
- [TODOs](#todos)

## Get Started

[Install Firmware](#install-firmware)  
[Building your own Rhythmboard from hardware](#build-from-hardware)  
[BOM](#bom)

### Install Firmware
<details>

<summary>If you're familiar with developing RP2040 microcontrollers or Raspberry Pi Pico, click here for a shorter explanation.</summary>

1. Go to the `Actions` tab.
2. Click the latest workflow run.
3. Find the `Artifacts` section, locate `firmware`, and click the download icon on the right to download `firmware.zip`.
   **If you can't find the `Artifacts` section**, click [here](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346).
4. Connect your board to your computer in BOOTSEL mode (by plugging in the RP2040-Zero while holding the BOOT button).
5. Unzip the `firmware.zip` you just downloaded and find the `.uf2` file inside.
6. Drag and drop the `.uf2` file into the RP2040-Zero USB drive (likely named `RPI-RP2`), and you're good to go.

---

</details>

1. Go to the `Actions` tab.
2. Click the latest workflow run.
3. Find the `Artifacts` section, locate `firmware`, and click the download icon on the right to download `firmware.zip`.
   **If you can't find the `Artifacts` section**, click [here](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346).
4. Press and hold the `BOOT` button on the RP2040-Zero. **DO NOT RELEASE** it before plugging the RP2040-Zero into your computer. Once plugged in, release the button. You should see a new USB device appear on your computer, likely named `RPI-RP2`.
5. Unzip the `firmware.zip` you just downloaded, locate the `.uf2` file in the extracted folder, and drag or copy it into the USB drive that appeared in the previous step.
6. Once the copy is complete, the USB drive will automatically disconnect, and the RP2040-Zero will reboot. Your Rhythmboard is now ready to use with the latest features available.

### Build from hardware

#### BOM

- RP2040-Zero x 1
- Machined Pin Header (23 pins in total: 9 pins x 2 + 5 pins)
- Machined Female Header (23 pins in total: 9 pins x 2 + 5 pins)
- MX profile mechanical switch hotswap socket x 17
- 1N4148W diode (SOD-123 package) x 17

- MX profile mechanical switch x 17
- Keycaps
  - 1u x 12
  - 1.25u x 1
  - 1.5u x 2
  - 2.25u x 2
- 2u PCB mount stabilizers x 2

#### 1. Prepare and Print PCB

1. Find the Gerber `.zip` file [here](/PCB/RhythmGameControllerKiCad/production/Gerber.zip).
2. Find a PCB manufacturer to make your PCB.
   [JLCPCB](https://jlcpcb.com/) is what I use and have tested. PCB Assembly (PCBA) is supported with the given files, but it might not be supported by other manufacturers. If you prefer other manufacturers and wish to use a PCBA service, please configure the necessary files yourself.
   *Not sponsored, but open to sponsorships from anyone (not limited to JLCPCB LOL).*
   > For the files required by JLCPCB PCBA: the BOM file is located at [/PCB/RhythmGameControllerKiCad/production/bom.csv](/PCB/RhythmGameControllerKiCad/production/bom.csv), and the placement/CPL file is located at [/PCB/RhythmGameControllerKiCad/production/positions.csv](/PCB/RhythmGameControllerKiCad/production/positions.csv).
3. Place your order and wait for your PCB to arrive.

#### 2. Solder Everything

Although I used a PCBA service for the SMD parts, if you are hand-soldering, it is recommended to solder the diodes first, followed by the switch sockets.

For THT parts, the workflow I chose is to solder the machined pin headers onto the RP2040-Zero first. Then, use the RP2040-Zero to confirm and adjust the angle before soldering the machined pin sockets onto the PCB.

#### 3. Assembly

1. Mount the stabilizers.
2. Mount the RP2040-Zero.
3. Place the switches.
4. Mount the keycaps. <!-- Note: add plate and case installation from here -->

#### 4. Install Firmware

Install the firmware onto your RP2040-Zero by following the steps written [here](#install-firmware).

## Default keymap

Layer 0 (default)
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">ZMK<br>Studio</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">Alt+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">W</td>
    <td align="center">E</td>
    <td align="center">R</td>
    <td align="center">T</td>
    <td align="center">U</td>
    <td align="center">I</td>
    <td align="center">O</td>
    <td align="center">P</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">G</td>
    <td align="center">J</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">G</td>
    <td colspan="2" align="center">J</td>
  </tr>
</table>

Layer 1
<table>
  <tr>
    <td width="12.5%" align="center">1</td>
    <td width="12.5%" align="center">ZMK<br>Studio</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">to 3</td>
    <td width="12.5%" align="center">2</td>
  </tr>
  <tr>
    <td align="center">F10</td>
    <td align="center">L⇧</td>
    <td align="center">↑</td>
    <td align="center">↓</td>
    <td align="center">←</td>
    <td align="center">→</td>
    <td align="center">R⇧</td>
    <td align="center">F11</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">A</td>
    <td align="center">↹</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">␣</td>
    <td colspan="2" align="center">↵</td>
  </tr>
</table>

<details>
<summary> Layer 2 (Layer transportation) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">to 0</td>
    <td width="12.5%" align="center">to 1</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">to 0</td>
    <td width="12.5%" align="center">to 0</td>
  </tr>
  <tr>
    <td align="center">to 3</td>
    <td align="center">to 4</td>
    <td align="center">to 5</td>
    <td align="center">to 6</td>
    <td align="center">to 7</td>
    <td align="center">to 8</td>
    <td align="center">to 9</td>
    <td align="center">to 10</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">none</td>
    <td align="center">none</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 0</td>
    <td></td>
    <td colspan="2" align="center">none</td>
    <td colspan="2" align="center">none</td>
  </tr>
</table>
</details>

<details>
<summary> Layer 3 (QWERTY DFJK default layout that's the default for most games) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">A</td>
    <td align="center">S</td>
    <td align="center">D</td>
    <td align="center">F</td>
    <td align="center">J</td>
    <td align="center">K</td>
    <td align="center">L</td>
    <td align="center">;</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">V</td>
    <td align="center">N</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">V</td>
    <td colspan="2" align="center">N</td>
  </tr>
</table>
</details>

<details>
<summary> Layer 4 (Hotkeys pad) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">A</td>
    <td align="center">X</td>
    <td align="center">C</td>
    <td align="center">V</td>
    <td align="center">Z</td>
    <td align="center">N</td>
    <td align="center">HOME</td>
    <td align="center">END</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">LALT</td>
    <td align="center">LGUI</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 2</td>
    <td></td>
    <td colspan="2" align="center">LCTRL</td>
    <td colspan="2" align="center">LSHIFT</td>
  </tr>
</table>
</details>

<details>
<summary> Layer 5~10 (user define) </summary>
<table>
  <tr>
    <td width="12.5%" align="center">ESC</td>
    <td width="12.5%" align="center">none</td>
    <td colspan="4"></td>
    <td width="12.5%" align="center">ALT+F9</td>
    <td width="12.5%" align="center">`</td>
  </tr>
  <tr>
    <td align="center">W</td>
    <td align="center">E</td>
    <td align="center">R</td>
    <td align="center">T</td>
    <td align="center">U</td>
    <td align="center">I</td>
    <td align="center">O</td>
    <td align="center">P</td>
  </tr>
  <tr>
    <td colspan="3"></td>
    <td align="center">G</td>
    <td align="center">J</td>
    <td></td>
    <td colspan="2" rowspan="2"></td>
  </tr>
  <tr>
    <td align="center">to 1</td>
    <td></td>
    <td colspan="2" align="center">G</td>
    <td colspan="2" align="center">J</td>
  </tr>
</table>
</details>

### Customize your keymap

1. Press the "ZMK Studio" key.
2. Go to [ZMK Studio](https://zmk.studio/).
3. Your browser may display a COM port connection pop-up (at least Chromium-based browsers do). Select the COM port your Rhythmboard is connected to. (It's not going to be COM1 or COM2 on Windows).
4. Customize your key bindings, keymaps, and layers on ZMK Studio as you want.
   > ⚠️ Note: Wireless-related options are not supported.

## TODOs
<!-- TODO: -->
- Upload plate file 
- Create its case <!-- Note: Need to edit #### 3. Assembly after uploaded -->

---

Developed based on [theArnoll/ZMK-4x3-Keyboard](https://github.com/theArnoll/ZMK-4x3-Keyboard)**