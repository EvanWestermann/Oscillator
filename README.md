# Oscillator

Oscillator is a browser‑based audiovisual synthesizer inspired by vintage oscilloscopes, vector displays, and analog signal processors. It combines Web Audio oscillators or external audio input with real‑time XY and waveform visualization, rendered as layered RGB traces with depth, drift, and distortion.

The entire application runs client‑side using standard web technologies (HTML, CSS, JavaScript, Web Audio API, and Canvas). No backend, build step, or external dependencies are required.

---

## Overview

Oscillator functions as a hybrid audio generator and signal visualizer:

* **Internal mode**: Dual hardware‑style oscillators generate stereo signals.
* **External mode**: User‑supplied audio files are processed and visualized.
* **Visualization modes**: 3D‑styled XY vector display or traditional waveform view.
* **Aesthetic goal**: Emulate CRT oscilloscope behavior with scanlines, phosphor glow, drift, and RGB separation.

All processing and rendering are real‑time and interactive.

---

## Features

### Audio Engine

* Dual oscillators (Primary / Secondary)
* Adjustable frequency per oscillator (20–880 Hz)
* Oscillator waveforms: Sine and Sawtooth
* Stereo panning for spatial separation
* External audio file support (local audio files)
* Saturation / distortion stage (waveshaper)
* Low‑pass filtering
* Master output gain control

### Visualization Engine

* Canvas‑based real‑time rendering
* Stereo signal analysis via AnalyserNode
* RMS‑based level meter
* RGB trace layering with additive blending
* Perspective‑based Z‑warp depth
* Drift and motion modulation
* Adjustable trace separation (horizontal or vertical depending on mode)

### UI / Interaction

* Power‑gated AudioContext initialization
* Hardware‑inspired tactile controls
* Visual feedback for active states
* CRT grid overlays and scanline effects

---

## Controls

### System Section

* **Power (⏻)**

  * Initializes or suspends the Web Audio context.
  * Required before any sound or visualization occurs.

* **Source Selector**

  * `OSC`: Internal oscillators
  * `EXT`: External audio file input

* **[INJECT]**

  * Appears when EXT is selected.
  * Allows loading a local audio file (MP3, WAV, etc.).

* **Output Level**

  * Controls master audio output volume.
  * Also scales visual intensity.

---

### Processing Section

* **Signal Balance**

  * Mix between dry and processed external audio signal.

* **Saturate (Drive)**

  * Controls distortion intensity applied via waveshaping.

---

### Oscillators Section

* **Primary Frequency (X)**

  * Sets the frequency of the left‑panned oscillator.

* **Secondary Frequency (Y)**

  * Sets the frequency of the right‑panned oscillator.

* **Waveform Selector**

  * SIN: Sine wave
  * SAW: Sawtooth wave

---

### Dimensions Section

* **Z‑Warp Depth**

  * Controls perspective distortion applied to traces.

* **Trace Offset**

  * Separates RGB traces spatially:

    * Horizontal separation in XY mode
    * Vertical separation in WAVE mode

* **Mode Selector**

  * `3D XY`: Vector‑style oscilloscope display
  * `WAVE`: Traditional waveform view

---

## Visualization Modes

### 3D XY Mode

* Left channel mapped to X axis
* Right channel mapped to Y axis
* Depth modulation creates pseudo‑3D perspective
* RGB traces are phase‑offset for motion richness

### WAVE Mode

* Combined stereo signal displayed over time
* RGB traces layered vertically when offset is applied
* Emphasizes amplitude and rhythmic structure

---

## Technical Architecture

### Core Technologies

* HTML5
* CSS3 (custom properties, gradients, overlays)
* Canvas 2D API
* Web Audio API

### Key Web Audio Nodes

* `AudioContext`
* `OscillatorNode`
* `GainNode`
* `WaveShaperNode`
* `BiquadFilterNode`
* `AnalyserNode`
* `StereoPannerNode`
* `MediaElementSourceNode`

### Rendering Pipeline

1. Audio signal routed to analyzers
2. Time‑domain data sampled each animation frame
3. RMS calculated for level metering
4. Traces rendered via additive blending (`screen` mode)
5. CRT effects layered above canvas

---

## Browser Requirements

* Modern Chromium‑based browser or Firefox
* Web Audio API support
* User interaction required to start audio (browser security policy)

Safari is supported but may exhibit stricter autoplay and AudioContext resume behavior.

---

## Usage Notes

* Audio will not start until the Power button is pressed.
* External audio never leaves the user’s device.
* Performance scales with canvas resolution and FFT size.
* Best experienced with headphones or stereo speakers.

---

## Concept & Inspiration

Oscillator draws inspiration from:

* Analog oscilloscopes
* Vector arcade displays
* Early digital signal processors
* CRT phosphor behavior
* Windows Media Player visualizer

It is intended as both a visual instrument and an interactive art piece.

---

## License

This project is provided as‑is for educational, artistic, and experimental use. No warranty is expressed or implied.
