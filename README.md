# Awesome Eurorack [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of open source Eurorack modular synthesizer resources — hardware designs, firmware, software tools, and development libraries.

Eurorack is the dominant modular synthesizer format, and its open-source community produces an extraordinary range of freely shared hardware designs, firmware, and tools. This list collects those resources, organized by module function, so you can quickly find open oscillators, filters, sequencers, and more — whether you are building your first module or seeking inspiration for your next design. Each entry is tagged with `HW` (hardware design files), `FW` (firmware/embedded code), or `SW` (software tools) to indicate what open-source material is available. Contributions and corrections are welcome.

**What qualifies as open source:** Any public GitHub repository with accessible source files — hardware design files (KiCad/Eagle schematics and PCB layouts), firmware source code, or software source code. A formal OSI-approved license is not required, but source files must be publicly viewable. Projects with only compiled binaries or documentation do not qualify.

**What qualifies as Eurorack:** The module or project must be specifically designed for the Eurorack format: 3U (128.5mm) panel height, power via ±12V Doepfer-compatible header, 3.5mm mono patch jacks. Multi-format projects are included only if Eurorack is the primary or explicitly documented target format.

**Archived and unmaintained projects:** Included with an `[Archived]` label in the description. Hardware designs age well; firmware may have dependency rot, but the design remains valuable.

**Partially open projects:** Included if hardware files (schematics, PCB) are publicly available, even if firmware or software is proprietary. Tagged with only the applicable type tags (e.g., `HW` only if firmware is closed).

## Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Oscillators](#oscillators)
- [Filters](#filters)
- [VCAs](#vcas)
- [Envelopes / Function Generators](#envelopes--function-generators)
- [Sequencers](#sequencers)
- [Modulation](#modulation)
- [Effects](#effects)
- [Utilities](#utilities)
- [MIDI / Digital Interfaces](#midi--digital-interfaces)
- [Power](#power)
- [Development Tools](#development-tools)
- [Standards and Specifications](#standards-and-specifications)
- [Learning Resources](#learning-resources)
- [Communities](#communities)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Oscillators

- [Clatters Sibilla](https://github.com/Clatters/Sibilla) `FW` - Digital stereo oscillator for Eurorack built on a DSP platform, with firmware source and resources for alternative firmware development.
- [Mutable Instruments Braids](https://github.com/pichenettes/eurorack/tree/master/braids) `HW` `FW` - Digital macro-oscillator with 16 synthesis algorithms. Part of the Mutable Instruments open-source collection.
- [Mutable Instruments Plaits](https://github.com/pichenettes/eurorack/tree/master/plaits) `HW` `FW` - Successor macro-oscillator with 16 synthesis models spanning digital, physical modeling, and analog-style generation.
- [Mutable Instruments Rings](https://github.com/pichenettes/eurorack/tree/master/rings) `HW` `FW` - Physical modeling resonator oscillator based on modal synthesis techniques.
- [Zlosynth Achordion](https://github.com/zlosynth/achordion) `HW` `FW` - Chord-crafting quantizing wavetable oscillator for Eurorack with open hardware and firmware.

## Filters

- [BleepSound MS20 VCF](https://github.com/BleepSound/ms20-vcf-simple) `HW` - MS20-style voltage-controlled filter for Eurorack with full KiCad schematics and PCB layout.
- [Mutable Instruments Ripples](https://github.com/pichenettes/eurorack/tree/master/ripples) `HW` `FW` - Resonant multimode filter with 24dB/oct low-pass, band-pass, and high-pass outputs.
- [Mutable Instruments Shelves](https://github.com/pichenettes/eurorack/tree/master/shelves) `HW` `FW` - Four-band equalizer filter module with voltage-controlled frequency and gain.

## VCAs

- [BleepSound Basic VCA](https://github.com/BleepSound/basic_vca) `HW` - Open hardware voltage-controlled amplifier for Eurorack with full KiCad schematics and PCB layout.
- [Mutable Instruments Veils](https://github.com/pichenettes/eurorack/tree/master/veils) `HW` `FW` - Quad VCA with switchable linear and exponential response curves.

## Envelopes / Function Generators

- [BleepSound Basic ADSR](https://github.com/BleepSound/basic_adsr) `HW` - Open hardware ADSR envelope generator for Eurorack with full KiCad schematics and PCB layout.
- [Mutable Instruments Peaks](https://github.com/pichenettes/eurorack/tree/master/peaks) `HW` `FW` - Dual function generator providing envelopes, LFOs, and tap tempo sequencing with a shared control interface.
- [Mutable Instruments Stages](https://github.com/pichenettes/eurorack/tree/master/stages) `HW` `FW` - Multistage envelope generator with chainable segment groups for complex shapes.

## Sequencers

- [Monome Teletype](https://github.com/monome/teletype) `HW` `FW` - Algorithmic scene-based sequencer with a command language interpreter.
- [Pangrus BPD](https://github.com/pangrus/bpd) `HW` `FW` - Beat pattern device sequencer module for Eurorack with open hardware and firmware.
- [TruthTable](https://github.com/attoparsec/TruthTable) `HW` - Eurorack logic and boolean truth table sequencer module with open hardware design files.

## Modulation

- [Erica Synths DIY](https://github.com/erica-synths/diy-eurorack) `HW` `FW` - Open source hardware and firmware for Erica Synths DIY Eurorack modules including LFOs and CV generators.
- [Mutable Instruments Tides](https://github.com/pichenettes/eurorack/tree/master/tides) `HW` `FW` - Tidal modulator functioning as macro-oscillator, LFO, and function generator with four simultaneous output modes.
- [Rheslip Eurorack Quad LFO](https://github.com/rheslip/Eurorack-Quad-LFO-Module) `HW` `FW` - Four-channel low frequency oscillator module with independent rate controls and open hardware design.

## Effects

- [Emeb RP2040 Audio](https://github.com/emeb/RP2040_Audio) `HW` `FW` - Eurorack stereo audio effects module based on the Raspberry Pi RP2040 microcontroller with open hardware and firmware.
- [Kxmx Bluemchen](https://github.com/recursinging/kxmx_bluemchen) `HW` `FW` - Eurorack effects module built on the Electrosmith Daisy Seed DSP platform with open hardware and firmware.
- [Modularev Nemesis](https://github.com/modularev/Nemesis) `HW` `FW` - Open source stereo reverb module for Eurorack with multiple algorithms.

## Utilities

- [Ghostintranslation modules](https://github.com/ghostintranslation) `HW` `FW` - Collection of open source Eurorack utility and interface modules.

## MIDI / Digital Interfaces

- [Newdigate Teensy Control Voltage](https://github.com/newdigate/teensy-control-voltage) `SW` `FW` - Teensy-based library for generating control voltage signals from MIDI.

## Power

- [Modulove modules](https://github.com/modulove) `HW` - Open source Eurorack module hardware including power distribution solutions.

## Development Tools

- [Eurorack Panel Designer](https://github.com/THX2112/Eurorack-Panel-Designer) `SW` - Web-based tool for designing Eurorack module front panels.

## Standards and Specifications

- [Printable Instruments](https://github.com/30350n/printable-instruments) `HW` - Printable panel and component files for open source Eurorack modules.

## Learning Resources

- [North Coast Modular Collective](https://github.com/NorthCoastModularCollective) `HW` `FW` - Open source Eurorack module designs with documentation aimed at DIY builders.

## Communities

- [QuinnFreedman Modular](https://github.com/QuinnFreedman/modular) `HW` `FW` - Community-oriented collection of open source Eurorack module designs.

## Contributing

Contributions welcome! Please read the [contribution guidelines](contributing.md) first.
