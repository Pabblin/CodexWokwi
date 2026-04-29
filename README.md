# Raspberry Pi Pico W Keypad-to-LED Controller

This repository documents and organizes a Raspberry Pi Pico/Pico W project where a 4x4 membrane keypad controls 12 LEDs.

> Core firmware logic is preserved exactly as provided (Arduino-style `setup()` / `loop()` using `Keypad.h`).

## Project Structure

```text
.
├── CMakeLists.txt
├── include/
├── src/
│   ├── CMakeLists.txt
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Features

- 4x4 matrix keypad input scanning.
- 12 independent LED outputs.
- Group ON/OFF commands for numeric LEDs (`9`/`0`) and letter LEDs (`*`/`#`).
- Deterministic mapping from each key to one LED action.

## Hardware Summary

- **MCU**: Raspberry Pi Pico / Pico W (RP2040)
- **Input**: 4x4 membrane keypad (rows/columns)
- **Outputs**: 12 LEDs (8 blue + 4 red), each with 220 Ω series resistor
- **Extra pull-ups**: 4× 1 kΩ pull-ups on keypad rows to 3V3 (as in diagram)

Detailed wiring and pin table: [`docs/wiring.md`](docs/wiring.md)

## Firmware Source

- Main firmware: [`src/main.cpp`](src/main.cpp)
- Uses Arduino APIs and `Keypad` library.

## Run in Wokwi

1. Create a new **Raspberry Pi Pico (or Pico W)** simulation in Wokwi.
2. Paste `src/main.cpp` into the sketch.
3. Use the provided `diagram.json` wiring from your project (or wire according to `docs/wiring.md`).
4. Ensure the **Keypad library** is available in the simulation environment.
5. Start simulation and press keypad keys to toggle LEDs.

## Run on Real Hardware

1. Assemble wiring exactly as described in [`docs/wiring.md`](docs/wiring.md).
2. Use an Arduino-compatible RP2040 core/toolchain (e.g., Arduino IDE with RP2040 core).
3. Install `Keypad` library.
4. Select board: **Raspberry Pi Pico W**.
5. Build and flash.

## About Pico SDK vs Arduino

The provided logic is Arduino-framework code (`Keypad.h`, `pinMode`, `digitalWrite`, `setup`, `loop`).
This repository keeps behavior unchanged and organizes documentation. A full native Pico SDK migration is intentionally **not** performed here to avoid logic/behavior drift.

## Wi-Fi Notes

- Pico W Wi-Fi is **not used** by the provided firmware.
- No credentials are required or stored.

