# Wiring and GPIO Mapping (Raspberry Pi Pico / Pico W)

## Components List (from provided `diagram.json`)

- 1× Raspberry Pi Pico (`wokwi-pi-pico`)
- 1× 4x4 membrane keypad (`wokwi-membrane-keypad`)
- 12× LEDs
  - 8× blue (`led1..led8`, labels 8..1)
  - 4× red (`led9..led12`, labels A..D)
- 12× 220 Ω resistors for LEDs (`r1..r12`)
- 4× 1 kΩ resistors as keypad row pull-ups (`rp1..rp4`)

## Keypad Connections

| Keypad Signal | Pico GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

> Diagram also shows R1..R4 each tied through 1 kΩ pull-up network to 3V3.

## LED Connections

Each LED anode is connected to a GPIO through a 220 Ω resistor. Each LED cathode goes to GND.

| Logical LED Index (`ledPins[]`) | Function Label | Pico GPIO |
|---:|---|---|
| 0 | 1 | GP11 |
| 1 | 2 | GP10 |
| 2 | 3 | GP9 |
| 3 | 4 | GP8 |
| 4 | 5 | GP7 |
| 5 | 6 | GP6 |
| 6 | 7 | GP5 |
| 7 | 8 | GP4 |
| 8 | A | GP3 |
| 9 | B | GP2 |
| 10 | C | GP28 |
| 11 | D | GP27 |

## UART / Serial Monitor

- GP0 → Serial RX (Wokwi monitor)
- GP1 → Serial TX (Wokwi monitor)

(Used by simulator wiring; not used in sketch logic.)

## Behavioral Mapping Summary

- `1..8` → turn ON corresponding LED index `0..7`
- `9` → turn ON LEDs `0..7`
- `0` → turn OFF LEDs `0..7`
- `A..D` → turn ON LEDs `8..11`
- `*` → turn ON LEDs `8..11`
- `#` → turn OFF LEDs `8..11`

## Assumptions / Notes

- The provided diagram targets `wokwi-pi-pico`; this wiring is valid for Pico W GPIO as well.
- No Wi-Fi hardware path is used in the current design.
