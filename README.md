# MICA

MICA is a Multi-Instrument Control and Automation program initially created for physicists performing nanoelectronics measurements.

MICA originated from a LabVIEW program that has been extensively used in the Condensed Matter Physics Group at the University of Manchester. The creator of MICA, a former PhD student in the group, received a copy of the LabVIEW program. After more than 5 years of use and numerous modifications, the program was almost completely rewritten to create MICA.

## Design of MICA

MICA features an easy-to-use GUI, and this repository was primarily created to share MICA and assist new students who want to automate their experiments without the need for advanced coding skills.

MICA was designed with extensibility and flexibility in mind, drawing inspiration from similar programs/frameworks such as [Labber](https://www.keysight.com/us/en/products/software/application-sw/labber-software.html) and [QCoDes](https://github.com/microsoft/qcodes).

MICA aims to provide wide support for instruments used in nanoelectronics and optoelectronic research. Take MICA with you and enjoy seamless measurement across different experiment stations, research groups, and labs.

## Get MICA

### First-time User

If you are trying MICA for the first time, you can download the latest version in the release page and follow the Usage Guide.

### Update MICA

If you already have MICA installed, you can check for announcements and new releases within the MICA program (work in progress).

## Cite MICA

If you find MICA helpful for your work, please cite MICA using the Zenodo link (to be determined).

## What can MICA do?

### Basics

MICA communicates with instruments via GPIB/Serial/Ethernet cables, allowing users to change instrument parameters (e.g., output voltage/current, frequency/amplitude of a lock-in, wavelength of a monochromator, temperature, magnetization, etc.) and perform measurements by reading parameters from the instruments.

To conduct an experiment using MICA, you need to know what to measure (Channel Configuration) and how to measure it (Measure Mode).

### Channel Configuration

Channel Configuration is a JSON text file that defines several channels, which represent the instrument parameters that MICA can change (input) and read (output). Each channel contains detailed information about the instrument hardware, such as address, instrument model, parameter type, etc.

Fortunately, MICA provides an Editor GUI that allows you to configure the channels. Additionally, example configuration files that have been used in various research groups are included.

### Measure Mode

Measure Mode defines how you want to change the input channels. MICA reads the output channels after each input change. MICA currently supports three measure modes: Manual, Sweep, and Map.

In Manual mode, MICA periodically reads the output channels, even if none of the input channels have changed. Changes to the input take effect immediately.

In Sweep mode, you can linearly change the value of an input channel step-by-step. At each step, MICA reads the current sweep-step value and the output channels, and then changes the input value to the next step value. Circular sweep is also supported.

Map Mode is a 2D Sweep, where you can linearly change the values of two input channels. These two channels are known as the fast-sweep axis and slow-sweep axis. In each slow-sweep step, the slow-sweep axis value remains fixed while the fast-sweep axis undergoes a full sweep. Afterward, the slow-sweep axis moves to the next step value.

### Supported Instruments

- Keithley
    - [2182 Nano-voltmeter](https://www.tek.com/en/products/keithley/low-level-sensitive-and-specialty-instruments/nanovoltmeter-model-2182a)
    - [2400 series Sourcemeter](https://www.tek.com/en/products/keithley/source-measure-units/2400-standard-series-sourcemeter)
    - [2450 Graphical series Sourcemeter](https://www.tek.com/en/products/keithley/source-measure-units/2400-graphical-series-sourcemeter)
    - [2600 series Sourcemeter](https://www.tek.com/en/products/keithley/source-measure-units/2600b-series-sourcemeter)
    - [4200-SCS Parameter Analyzer](https://www.tek.com/en/products/keithley/4200a-scs-parameter-analyzer)
    - [6200 series Current Source Supply](https://www.tek.com/en/products/keithley/low-level-sensitive-and-specialty-instruments/series-6200)
- Keysight
    - [B2900 series Sourcemeter](https://www.keysight.com/us/en/products/source-measure-units-smu/b2900-series-precision-source-measure-units-smu.html)
- Stanford Research Systems
    - [SR830 Lock-in Amplifier](https://www.thinksrs.com/products/sr830.html)
    - [SR865A Lock-in Amplifier](https://thinksrs.com/products/sr865a.html)
- Lakeshore
    - [LS336 Temperature controller](https://www.lakeshore.com/products/categories/overview/temperature-products/cryogenic-temperature-controllers/model-336-cryogenic-temperature-controller)
- Quantum Design
    - [Dynacool PPMS](https://www.qdusa.com/products/dynacool.html)
- [Oxford TeslatronPT](https://nanoscience.oxinst.com/dry-systems/products/teslatronpt)
    - [Mercury iTC Temperature Controller](https://nanoscience.oxinst.com/accessories/mercuryitc)
    - [Mercury iTC-HelioxVT](https://nanoscience.oxinst.com/products/helioxvt)
    - [Mercury iPS Magnet Power Supply](https://nanoscience.oxinst.com/accessories/mercuryips)
- Ophir Laser Measurement
    - [NOVA II Laser Power Meter](https://www.ophiropt.com/en/f/nova-2-power-meter)
- Zolix (卓立汉光)
    - OminiL Spec SDK (Monochrometre Wavelength/Grating and Shutter)

## What can't MICA do?

### MICA does not automate everything

MICA's support for instrument configuration is limited. You still need to set up all the instrument connections, know how to check instrument addresses, and most importantly, manually configure each instrument on the hardware panel (e.g., range, compliance, enable output, etc.).

### MICA does not handle connection errors properly

When MICA works, it works well, as it serves a simple purpose. However, new users often encounter difficulties with instrument connections and communication between instruments and their PC. It is important to note that MICA may not provide sufficient assistance in resolving communication issues.

### MICA does not guarantee safety (especially for your devices)

Before using MICA, you should ensure that the instrument connections are correct, the instruments are properly configured, and all signals are checked. It is recommended to run a sweep manually and have a good understanding of what and how to run any MICA Measure Mode. **USE AT YOUR OWN RISK**.

### MICA does not fully support all the Supported Instruments

MICA is a work in progress and currently supports only some common functionalities required by the initial research groups that use MICA.

### Anything else not covered here

If you encounter a bug or need a new feature, please create an issue.

## Usage Guide

### Try with No Instrument

### Try with Keithley 2600 series

### More Details
For more detailed information, please read the full user manual [here]().

## In the End

This repository hosts the released versions and documentation of MICA, example channel configuration files, and the source code of an Updater module (work in progress). Since MICA is still a work in progress, the source code of MICA will remain privately maintained for now. There are plans to open-source and release the driver layer as an independent LabVIEW Package as well as some other modules.
