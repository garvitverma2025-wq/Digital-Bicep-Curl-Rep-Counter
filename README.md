# Digital Bicep Curl Repetition Counter Using Logic ICs

An IC-based bicep curl repetition counter developed as a Digital Logic Design project. The system uses a tilt sensor to detect changes in dumbbell orientation and digital logic ICs to process and display the repetition count, without Arduino or a microcontroller.

## Project Overview

The project demonstrates how basic digital electronics can be combined to build a simple exercise repetition counter. The tilt sensor detects changes in orientation during a curl movement. Signal conditioning and pulse-generation stages interface the sensor with a digital counter, and the count can be displayed on a seven-segment display.

## Hardware Components

| Component | Intended role |
|---|---|
| Tilt sensor | Detects changes in dumbbell orientation |
| 7414 Schmitt Trigger | Signal conditioning |
| NE555 Timer | Pulse generation / timing |
| 7490 Decade Counter | Counts pulses |
| 7448 BCD-to-Seven-Segment Decoder | Drives the display |
| 7485 Magnitude Comparator | Compares the count with a target |
| Seven-segment display | Displays the repetition count |
| Resistors and capacitors | Biasing and timing components |
| Power supply | Provides circuit power |

> **Implementation note:** The component roles above describe the project design at a high level. Confirm exact wiring, timer configuration, comparator connections, and the completed-curl counting logic against the original hardware before treating this README as a verified circuit schematic.

## Functional Block Diagram

```text
Tilt Sensor
    |
    v
7414 Schmitt Trigger
    |
    v
NE555 Pulse / Timing Stage
    |
    v
7490 Decade Counter
    |
    v
7448 BCD-to-7-Segment Decoder
    |
    v
Seven-Segment Display

7485 Comparator: compares the count with a preset target
```

## Working Principle

1. The tilt sensor detects a change in the dumbbell's orientation.
2. The 7414 stage conditions the sensor signal.
3. The NE555 stage provides the intended timing or pulse-generation function.
4. The 7490 counter increments in response to valid counting pulses.
5. The 7448 decodes the BCD count for display on a seven-segment display.
6. The 7485 can be used to compare the current count with a preset target.

The detection and counting logic should be configured so that one complete curl is counted once, rather than counting both directions independently.

## Key Learning Outcomes

- Application of Schmitt triggers for digital signal conditioning.
- Use of a 555 timer in pulse-generation circuits.
- BCD counting using a decade counter.
- Interfacing a decoder with a seven-segment display.
- Magnitude comparison using a digital comparator.
- Integration of discrete logic ICs into a practical hardware system.

## Applications

- Basic workout repetition tracking.
- Digital electronics laboratory demonstrations.
- Educational demonstrations of counters and display interfacing.

## Limitations

- Detection depends on sensor orientation and mounting.
- Sudden movement or an unsuitable threshold may cause false counts.
- Reliable one-repetition detection requires appropriate signal conditioning and movement-cycle logic.

## Future Scope

- Add a buzzer or indicator for target completion.
- Extend the display to support larger counts.
- Improve filtering and movement-cycle detection.
- Adapt the design for other exercise movements.

## Repository Contents

Project photographs, a verified circuit diagram, detailed connection tables, and the final project report can be added as they become available.

## Disclaimer

This README is reconstructed from the available project details. It is not a verified record of every final circuit connection or measured result. Update the documentation with actual build photographs, tested values, and the final circuit before using it as a definitive hardware reference.
