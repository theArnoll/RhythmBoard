# Arnoll Rhythmboard 1

A easily customizable controller for the most computer rhythm games

Suitable for osu!, DJMAX RESPECT V, Quaver, vivid/stasis, Milthm, Rhythm Doctor, Sparebeat, Polylylyrhythm, Estella, In Falsus (theoretically), etc.  
The overall layout and default keymap is optimized for DJMAX RESPECT V, but anything

## Contents

- [Arnoll Rhythmboard 1](#arnoll-rhythmboard-1)
  - [Contents](#contents)
  - [Get Started](#get-started)
    - [Install Firmware](#install-firmware)
    - [Build from hardware](#build-from-hardware)
      - [BOM](#bom)
      - [1. Prepare and Print PCB](#1-prepare-and-print-pcb)
      - [2. Solder Everything](#2-solder-everything)
      - [3. Assembly](#3-assembly)
      - [4. Install Firmware](#4-install-firmware)
  - [TODOs](#todos)

## Get Started

[Install Firmware](#install-firmware)  
[Building your own Rhythmboard from hardware](#build-from-hardware)  
> [BOM](#bom)

### Install Firmware

<details>

<summary>If you're familiar with developing RP2040 micro controllers or Raspberry Pi Pico, click here for shorter explaination</summary>

1. Go to `Actions` tab
2. Click the latest one
3. Find `Artifacts` section, find `firmware`, click the download icon on the right to download `firmware.zip`
   **If you can't find the `Artifacts` section**, click [here](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346)
4. Get your board connect to your computer in BOOTSEL mode (by plug in the RP2040-Zero with BOOT button pressed)
5. Unzip the `firmware.zip` you just downloaded and find the `.uf2` file in it
6. Throw the `.uf2` into the RP2040-Zero USB drive and you're good to go (the USB drive is likely called `RPI-RP2`)

---

</details>

1. Go to `Actions` tab
2. Click the latest one
3. Find `Artifacts` section, find `firmware`, click the download icon on the right to download `firmware.zip`
   **If you can't find the `Artifacts` section**, click [here](https://github.com/theArnoll/RhythmBoard/actions/runs/27726159548/artifacts/7710387346)
4. Press the `BOOT` button on RP2040-Zero, **DO NOT RELEASE** before plug RP2040-Zero into your computer. After you plugged in, release the button. You should see a new USB device appear in your computer. The name of the USB device is likely to be `RPI-RP2`.
5. Unzip the `firmware.zip` you just downloaded, find `.uf2` file in the folder you just unzipped, and drag it or copy it into the USB drive that appeared in the previous step.
6. After copy finished, the USB drive should automatically unplug, and the RP2040-Zero should reboot, and your Rhythmboard should be able to use now with the latest function available.

### Build from hardware

#### BOM

 - RP2040-Zero x 1
 - Machined Pin Header (23 pins in total, 9 pins x 2 + 5 pins)
 - Machined Female Header (23 pins in total, 9 pins x 2 + 5 pins)
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

1. Find the Gerber `.zip` file [here](/PCB/RhythmGameControllerKiCad/production/Gerber.zip)
2. Find a PCB manufacturer make your PCB.
   [JLCPCB](https://jlcpcb.com/) is what I use and tested. PCB Assembly (PCBA) is supported with given files, but it shouldn't be supported with other manufacturer. If you prefer other manufacturer and wish to use PCB Assembly service, please work on everything about this by yourself.
   *Not sponsored, but open for sponsorships from anyone and not limited to JLCPCB LOL*
   > For the files JLCPCB PCBA needed, BOM file is located at [/PCB/RhythmGameControllerKiCad/production/bom.csv](/PCB/RhythmGameControllerKiCad/production/bom.csv), and placement file / CPL file is located at [/PCB/RhythmGameControllerKiCad/production/positions.csv](/PCB/RhythmGameControllerKiCad/production/positions.csv).
3. Place your order and wait for your PCB arrive

#### 2. Solder Everything

Althought I'm using PCBA service for SMD parts, but solider diode first, and then switch socket sounds legit.

For THT parts, machined pin header on RP2040-Zero, and then machined pin socket on PCB with RP2040-Zero confirm and adjust the angle of pin socket is the workflow I choose.

#### 3. Assembly

1. Mount stabilizers
2. Mount RP2040-Zero
3. Place switches
4. Mount keycaps <!-- Note: add plate and case installation from here -->

#### 4. Install Firmware

Install firmware into your RP2040-Zero with steps wrote [here](#install-firmware)

## TODOs
<!-- TODO: -->
 - Upload plate file 
 - Create its case <!-- Note: Need to edit #### 3. Assembly after uploaded -->

---

Developed based on [theArnoll/ZMK-4x3-Keyboard](https://github.com/theArnoll/ZMK-4x3-Keyboard)