# Firmware Architecture

## Overview

The project is a single-module, event-polling firmware:

1. Initialize all LED GPIO pins as outputs and drive LOW.
2. Poll keypad for key events in `loop()`.
3. Dispatch key action using a `switch` statement.
4. Apply GPIO writes to one LED or LED groups.
5. Delay 10 ms for scan pacing.

## Source Layout

- `src/main.cpp`
  - Pin/constant definitions
  - Keypad keymap and pin matrix binding
  - Runtime setup and polling loop

## Key Data Structures

- `keys[4][4]`: 4x4 character layout
- `ledPins[12]`: GPIO mapping for 12 LEDs
- `rowPins[4]`: keypad row GPIO pins
- `colPins[4]`: keypad column GPIO pins
- `Keypad keypad`: keypad driver object

## Control Flow

### `setup()`

- Iterates over `ledPins`
- Sets each pin mode `OUTPUT`
- Writes initial `LOW`

### `loop()`

- Calls `keypad.getKey()`
- If a key is pressed, handles action in `switch(key)`
- Uses direct `digitalWrite()` for single LEDs
- Uses `for` loops for group ON/OFF operations
- Waits `10 ms`

## Design Characteristics

- **Deterministic behavior**: one action path per key.
- **No dynamic allocation**: static arrays only.
- **No RTOS / interrupts**: cooperative polling loop.
- **No networking**: Pico W wireless block unused.

## Self-Critique and Improvement Pass

- **Initial draft concern**: ambiguity between Arduino-style source and native Pico SDK build workflow.
- **Improvement applied**: documentation now explicitly distinguishes runtime framework expectations while keeping firmware logic unchanged.

