![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/test/badge.svg)


# Large Language Model based Digital Clock Using Time Division Multiplexing

## Overview:
This project aims to design a digital clock using Verilog HDL (Hardware Description Language), Functionally verify  it on a Field Programmable Gate Array (FPGA) board and to submit for fabrication of its ASIC through Efabless' TinyTapeout shuttle 6 . The digital clock will display hours, minutes, and seconds on a 7-segment display using time division multiplexing technique. It leverages the capabilities of a language learning model like ChatGPT to generate the Verilog code for the clock module. Additionally, the project adheres to pinout constraints, ensuring compatibility withthe design constraints as per TinyTapeout's requirements. 

![image](https://github.com/HUZAIFA-TARIQ/GIKI-TapeOut-2/assets/90867361/828f4e6d-6ac7-4adb-a833-7e66fccc1fad)


## **Key Components:**

#### Verilog HDL:
Verilog is a hardware description language used to model digital systems. It allows designers to describe the behavior of digital circuits and their interactions.

#### Time Division Multiplexing (TDM): 
TDM is a technique used to share a single communication channel among multiple devices by dividing the channel into time slots. In this project, TDM is employed to cycle through the digits of the clock display rapidly, giving the illusion of simultaneous display of hours, minutes, and seconds.

#### ChatGPT:
ChatGPT is a language learning model capable of generating human-like text based on input prompts. In this project, ChatGPT is utilized to generate the Verilog code for the digital clock module based on the provided specifications and requirements.

###FPGA Board: 
FPGA boards provide a platform for implementing digital designs in hardware. They offer reconfigurability and flexibility, making them suitable for prototyping and development of digital systems. All functional verifcation of the design, prior to and after submission, was done using Nexys DDR-4 FPGA boards.

 ## Pinout Constraints:

The digital clock module is designed to adhere to pinout constraints or which "Time Division Multiplexing" is used to drive the 7-segment displays:

##### cll: clock 
##### rst: reset
##### 8 input pins: value set register input.
##### 8 output pins: for segment data output.
##### 8 bidirectional pins: 6 as anode select pins and 2 as value set selection input.

## Programmability:

The digital clock designed in this project offers programmability in terms of setting the values of hours, minutes, and seconds. This feature allows users to customize the time displayed by the clock according to their preferences or specific requirements. Here's how the programmability aspect works:

#### The Value Set Register:
The Value Set Register is a 8-bit register that stores data from 8 input pins. The upper 4 bits (MSB 4 Bits) store BCD value of "Tens" for Hours/Minutes/Seconds. The Lower 4 bits (LSB 4 Bits) store BCD value of "Units" for Hours/Minutes/Seconds.

#### Value Set Selection Input:
2 of the bidirectional IOs are used as an input port (2-Bit), designated for value set selection, allowing users to specify which part of the time (hours/minutes/seconds) they want to set. This input determines whether the incoming data should update the hours, minutes or seconds portion of the clock display as follows;
##### 2.1) Value Set Selection Input = 00: Run Clock
##### 2.2) Value Set Selection Input = 01: Set Minutes
##### 2.3) Value Set Selection Input = 10: Set Hours
##### 2.4) Value Set Selection Input = 11: Set Seconds

## Time Division Multiplexing and Anode Selection for Seven-Segment Display:

In the digital clock project, multiplexing and anode selection techniques are employed to efficiently drive multiple seven-segment displays using a minimal number of output pins. Here's a comprehensive explanation of how these techniques are utilized:

#### Multiplexing:
Multiplexing involves sequentially switching between multiple displays to show different digits of the clock without the need for individual output signals (8-pins) for each display. In our clock, time is displayed as tens and units of hours, minutes, and seconds, each requiring a seven-segment display.

#### Segment Data Generation:
The BCD (Binary-Coded Decimal) values representing each digit of the time are converted to the corresponding segment data required to display that digit on a seven-segment display. This data is stored and updated based on the current anode count.

#### Anode Selection:
Anode selection is a technique used to enable individual seven-segment displays in a multiplexed configuration. Each display has its own anode pin, which is connected to a common cathode pin of all the displays. By selectively enabling the anode of one display at a time, the desired digit can be illuminated without interference from other displays. Anode selection pins are bidirectional (configuers as outputs) and controlled by the clock module. Each anode select pin corresponds to a specific digit of the clock display (units and tens of hours/minutes/seconds). When the corresponding digit is being displayed, the respective anode select pin is activated to enable that particular display.

By combining multiplexing with anode selection, the digital clock efficiently utilizes its limited output pins to drive multiple seven-segment displays, providing a clear and accurate representation of time while minimizing hardware complexity and resource usage.

# Tiny Tapeout Verilog Project Template

- [Read the documentation for project](docs/info.md)

## What is Tiny Tapeout?

TinyTapeout is an educational project that aims to make it easier and cheaper than ever to get your digital designs manufactured on a real chip.

1. Add your Verilog files to the `src` folder.
2. Edit the [info.yaml](info.yaml) and update information about your project, paying special attention to the `source_files` and `top_module` properties. If you are upgrading an existing Tiny Tapeout project, check out our [online info.yaml migration tool](https://tinytapeout.github.io/tt-yaml-upgrade-tool/).
3. Edit [docs/info.md](docs/info.md) and add a description of your project.
4. Optionally, add a testbench to the `test` folder. See [test/README.md](test/README.md) for more information.

The GitHub action will automatically build the ASIC files using [OpenLane](https://www.zerotoasiccourse.com/terminology/openlane/).

## Enable GitHub actions to build the results page

- [Enabling GitHub Pages](https://tinytapeout.com/faq/#my-github-action-is-failing-on-the-pages-part)

## Resources

- [FAQ](https://tinytapeout.com/faq/)
- [Digital design lessons](https://tinytapeout.com/digital_design/)
- [Learn how semiconductors work](https://tinytapeout.com/siliwiz/)
- [Join the community](https://tinytapeout.com/discord)
- [Build your design locally](https://docs.google.com/document/d/1aUUZ1jthRpg4QURIIyzlOaPWlmQzr-jBn3wZipVUPt4)

## What next?

- [Submit your design to the next shuttle](https://app.tinytapeout.com/).
- Edit [this README](README.md) and explain your design, how it works, and how to test it.
- Share your project on your social network of choice:
  - LinkedIn [#tinytapeout](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout) [@TinyTapeout](https://www.linkedin.com/company/100708654/)
  - Mastodon [#tinytapeout](https://chaos.social/tags/tinytapeout) [@matthewvenn](https://chaos.social/@matthewvenn)
  - X (formerly Twitter) [#tinytapeout](https://twitter.com/hashtag/tinytapeout) [@matthewvenn](https://twitter.com/matthewvenn)
"# DigitalClock-TinyTapeout" 
"# DigitalClock-TinyTapeout" 
