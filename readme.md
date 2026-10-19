<!-- title -->

# Brain Grapher

<!-- /title -->

<!-- badges -->

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/license/mit)

<!-- /badges -->

<!-- description -->

**Processing-based visualizer for NeuroSky EEG brainwave data output from the Arduino Brain library.**

<!-- /description -->

## Overview

<img width="500" src="screenshot.jpg" alt="Brain Grapher showing EEG waveforms and channel monitors" />

Brain Grapher is a proof of concept for visualizing brainwave data over time. It reads comma-separated serial packets from an Arduino connected to a hacked MindFlex EEG headset, then displays signal quality, attention, meditation, and eight EEG power bands.

The interface provides per-channel graph toggles, four rendering modes, local or global scaling, a time-scale slider, and a connection-quality indicator.

## Getting started

### Dependencies

- [Processing](https://processing.org/download/), historically tested with version 3.0.2. Compatibility with newer versions has not been verified.
- [ControlP5 GUI Library](https://github.com/sojamo/controlp5) 2.2.5 is included with this project in the `/code` folder. No separate installation is needed.
- An Arduino connected over USB and a compatible EEG headset. The [Arduino Brain library](https://github.com/kitschpatrol/brain) provides the expected serial output, and the [hardware tutorial](https://frontiernerds.com/brain-hack) explains the MindFlex setup.

### Installation

1. Install the Arduino Brain library and upload its [BrainSerialTest example](https://github.com/kitschpatrol/brain/tree/main/examples/BrainSerialTest) to your Arduino.
2. Download or clone [this repository](https://github.com/kitschpatrol/brain-grapher).
3. Open [BrainGrapher/BrainGrapher.pde](BrainGrapher/BrainGrapher.pde) in the Processing editor. Keep the other `.pde` files and the `code` folder together inside `BrainGrapher`.

## Usage

### Selecting a serial port

The sketch prints the available serial ports and their indices in Processing's console when it starts. Find your Arduino in that list, then change the index in `setup()` to match:

```java
serial = new Serial(this, Serial.list()[0], 9600);
```

For example, use `Serial.list()[1]` for the port listed as `[1]`. Run the sketch again after changing the index. The Arduino must send data at **9600 baud**. Close other applications using that serial port, including the Arduino Serial Monitor.

### Serial data format

Each packet contains 11 comma-separated integers in this order, followed by a newline:

```text
signal quality,attention,meditation,delta,theta,low alpha,high alpha,low beta,high beta,low gamma,high gamma
```

Signal quality ranges from 0 (good signal) to 200 (no signal). Attention and meditation range from 0 to 100. The remaining eight values represent EEG power bands.

The sketch skips the first three packets to avoid initialization noise. When signal quality is 200, it zeros the eight EEG power values.

## Background

Created by Eric Mika at NYU ITP in spring 2010. Revised in spring 2012 for Processing and ControlP5 updates, in early 2014 to bundle dependencies and update ControlP5, and in spring 2016 to support Processing 3 and ControlP5 2.2.5.

The repository was originally named `Processing-Brain-Grapher`, became `BrainGrapher` in 2014, and is now hosted at [`kitschpatrol/brain-grapher`](https://github.com/kitschpatrol/brain-grapher).

<!-- license -->

## License

[MIT](license.txt) © [Eric Mika](https://ericmika.com)

<!-- /license -->

The bundled ControlP5 library is covered by its [own license](https://github.com/sojamo/controlp5/blob/master/LICENSE.md).
