# Digital Bicep Curl Repetition Counter Using Logic ICs

An IC-based bicep curl repetition counter developed as a Digital Logic Design (DLD) project. The system uses a tilt sensor to detect changes in dumbbell orientation and digital logic ICs to process and display the repetition count, without Arduino or a microcontroller.

## Project overview

The project demonstrates how basic digital electronics can be combined to build an exercise repetition counter. A tilt sensor detects orientation changes during a curl movement. Signal-conditioning and timing stages interface the sensor with a digital counter, and a BCD decoder drives a seven-segment display. A magnitude comparator is included for comparison with a preset target.

## Hardware components

| Component | Intended role |
|---|---|
| Tilt sensor | Detects changes in dumbbell orientation |
| 7414 Schmitt-trigger inverter | Signal conditioning |
| NE555 timer | Timing / pulse-generation stage |
| 7490 decade counter | Counts valid pulses |
| 7448 BCD-to-seven-segment decoder/driver | Drives the display |
| 7485 4-bit magnitude comparator | Compares a count with a preset value |
| Seven-segment display | Displays the repetition count |
| Resistors and capacitors | Biasing and timing |
| DC power supply | Powers the circuit |

> **Accuracy note:** This repository was reconstructed after the original report and build photographs were no longer available. Component roles are documented at a functional level. Exact pin connections, timer configuration, component values, display compatibility and measured results have not been independently verified. Do not treat the block diagram as a pin-to-pin schematic.

## Functional block diagram

```text
Tilt Sensor
    |
    v
7414 Schmitt-trigger stage
    |
    v
NE555 timing / pulse stage
    |
    v
7490 decade counter
    |
    v
7448 BCD-to-seven-segment decoder
    |
    v
Seven-segment display

7485 comparator: compares the count with a preset target
```

This is a functional overview, not a wiring diagram.

## Working principle

1. The tilt sensor detects a change in the dumbbell's orientation.
2. The 7414 stage conditions the sensor signal and provides a Schmitt-trigger transition.
3. The NE555 is used as a timing or pulse-generation stage; its exact mode must be confirmed from the built circuit.
4. The 7490 advances in response to valid counting pulses.
5. The 7448 converts the BCD count into segment-control signals for the display.
6. The 7485 can compare the current count with a preset target.

**One complete curl should produce one count.** The detection logic must distinguish a full movement cycle from its individual upward and downward transitions. This behaviour should be verified on the physical circuit.

## Documentation

- [Reconstructed project report](docs/PROJECT_REPORT.md)
- [Component reference guide](docs/COMPONENT_REFERENCE.md)
- [Hardware validation checklist](docs/VALIDATION_CHECKLIST.md)

## Key learning outcomes

- Signal conditioning using Schmitt-trigger logic.
- Timing and pulse generation using a 555 timer.
- BCD counting with a decade counter.
- Seven-segment display decoding.
- Magnitude comparison using a digital comparator.
- Integration of discrete logic ICs in a practical hardware prototype.

## Applications

- Basic workout repetition tracking.
- Digital electronics laboratory demonstrations.
- Educational demonstrations of counters, timing circuits and display interfacing.

## Limitations

- Tilt-based detection depends on sensor orientation and mounting.
- Sudden movement or vibration may cause false transitions.
- Accurate counting requires reliable pulse shaping and full-cycle detection.
- The available documentation does not yet include a verified as-built schematic or measured test results.

## Future improvements

- Improve filtering and movement-cycle detection.
- Add a target-reached indicator or buzzer, if implemented in the hardware.
- Extend the display for larger repetition counts.
- Adapt the sensor and detection logic for other exercise movements.
- Add actual build photographs, verified wiring and measured test results.

## Repository status

The report and component notes are reconstructed from the project details available. The original project report and photographs were not available during documentation. The validation checklist identifies what should be confirmed before publishing a definitive circuit diagram or performance claims.

## References

Refer to the manufacturer datasheets for the exact variants used:

- 7414 / 74x14 Schmitt-trigger inverter.
- NE555 timer.
- 7490 / 74x90 decade counter.
- 7448 BCD-to-seven-segment decoder/driver.
- 7485 4-bit magnitude comparator.
