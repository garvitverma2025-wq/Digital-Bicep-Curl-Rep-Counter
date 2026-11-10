# Digital Bicep Curl Repetition Counter Using Logic ICs

> **Documentation status:** Reconstructed from the project details available after the original report and photographs were lost. This document describes the intended design and known components; it is not a verified as-built schematic or test report. Replace the verification notes with observations from the actual hardware wherever possible.

## 1. Abstract

This project explores a hardware-based approach to counting bicep curl repetitions using a tilt sensor and discrete digital logic ICs. A change in dumbbell orientation is used as the movement input. Signal conditioning and pulse-generation stages interface that input to a digital counter, and a decoder drives a seven-segment display to show the count. A magnitude comparator is included in the design for comparison against a preset target.

The project demonstrates the practical use of digital signal conditioning, timing, BCD counting, display decoding and magnitude comparison without an Arduino or other programmable microcontroller.

## 2. Problem statement

Manual repetition counting can distract a person during exercise and may lead to missed or inaccurate counts. The aim is to develop a simple electronic demonstrator that detects dumbbell orientation changes and maintains a visible count of completed curl repetitions.

## 3. Objectives

- Detect dumbbell orientation changes using a tilt sensor.
- Condition the sensor signal to obtain a usable digital transition.
- Generate a suitable counting pulse.
- Count valid repetitions using a decade counter.
- Display the count on a seven-segment display.
- Provide a comparator stage for checking the count against a preset target.
- Implement the system using logic ICs rather than a microcontroller.

## 4. Known hardware

| Component | Intended role in the design |
|---|---|
| Tilt sensor | Detects changes in dumbbell orientation |
| 7414 Schmitt-trigger inverter | Signal conditioning and transition cleanup |
| NE555 timer | Timing or pulse-generation stage |
| 7490 decade counter | Counts input pulses in BCD/decade sequence |
| 7448 BCD-to-seven-segment decoder/driver | Converts the BCD count into display segment signals |
| 7485 4-bit magnitude comparator | Compares the count with a preset binary value |
| Seven-segment display | Presents the count to the user |
| Resistors and capacitors | Biasing and timing components |
| DC supply | Powers the circuit |

**Important:** The exact 555 configuration, sensor interface, component values, display type, reset arrangement and comparator wiring must be confirmed from the actual circuit. They are intentionally not guessed here.

## 5. Functional overview

The intended signal path is:

```text
Tilt Sensor
    |
    v
7414 Signal Conditioning
    |
    v
NE555 Timing / Pulse Stage
    |
    v
7490 Decade Counter
    |
    v
7448 BCD-to-7-Segment Decoder
    |
    v
Seven-Segment Display

7485 Comparator <--- Counter value and preset target
```

The diagram is a functional overview only. It does not represent pin-to-pin wiring.

## 6. Working principle

1. The tilt sensor responds to a change in the dumbbell's orientation.
2. The sensor output is interfaced to a 7414 Schmitt-trigger stage. Hysteresis can help produce a cleaner logic transition when the input changes slowly or is noisy.
3. The NE555 is used as a timing or pulse-generation stage. Its exact mode and timing values depend on the implemented circuit.
4. A valid pulse is applied to the 7490 counter, which advances its count.
5. The 7490's BCD output is connected to a 7448 decoder/driver.
6. The decoder drives the seven-segment display to show the count.
7. The 7485 comparator can compare the current count with a preset target and provide a greater-than, equal-to or less-than result.

### One curl must equal one count

A complete curl includes both the lifting and lowering portions of the movement. The sensor and pulse logic must be arranged so that the full movement cycle produces exactly one accepted count. If both transitions are counted, one curl may be registered twice. This is a key point to validate on the physical circuit.

## 7. Design considerations

- **Sensor mounting:** Fix the tilt sensor securely and consistently to the dumbbell or moving assembly.
- **Signal conditioning:** Check the idle and active sensor levels and confirm that the 7414 output has clean transitions.
- **Pulse shaping:** Ensure the 555 stage produces one well-defined pulse per intended event.
- **Counting:** Verify that the 7490 receives only one pulse per completed curl.
- **Display compatibility:** Confirm the display type and the 7448 datasheet's required segment polarity and connections.
- **Comparator width:** A 7485 compares four-bit values. Cascading or additional logic may be required for a wider count or target.
- **Power and decoupling:** Use the correct supply voltage for every IC and place decoupling capacitors close to the IC supply pins.

## 8. Testing and validation plan

Record actual results in this table after testing the hardware.

| Test | Procedure | Expected observation | Actual result |
|---|---|---|---|
| Power-on | Apply the specified supply | ICs power up without overheating | To be recorded |
| Sensor idle | Keep the dumbbell stationary | Stable sensor logic state | To be recorded |
| Sensor movement | Tilt the dumbbell through the intended movement | Repeatable state transitions | To be recorded |
| Signal conditioning | Observe the 7414 output | Clean logic-level transitions | To be recorded |
| Pulse stage | Observe the 555 output | One intended pulse for each accepted event | To be recorded |
| Counter | Apply known test pulses | Count advances correctly | To be recorded |
| Display | Check each count | Display matches the counter state | To be recorded |
| Full curl | Perform one complete curl | Exactly one increment | To be recorded |
| Target comparison | Apply a known count and preset value | Correct comparator relation | To be recorded |

Do not enter results as successful until they have been measured on the actual build.

## 9. Advantages

- Demonstrates digital electronics using discrete logic ICs.
- Does not require a programmable microcontroller.
- Makes the count visible on a seven-segment display.
- Combines sensing, timing, counting and comparison concepts in one application.

## 10. Limitations

- A tilt sensor detects orientation changes, not muscle activity or exercise form.
- Sensor placement and movement speed can affect repeatability.
- A simple two-state sensor may generate more than one transition during a movement cycle.
- Accurate repetition counting depends on suitable pulse shaping and cycle-detection logic.
- The documented circuit details need to be checked against the final physical implementation.

## 11. Future improvements

- Improve rejection of vibration and accidental movement.
- Add a clear target-reached indicator or buzzer if implemented.
- Extend the display for larger repetition counts.
- Adapt the sensor mounting and detection logic for other exercises.
- Add measured test results and photographs to the repository.

## 12. Conclusion

The Digital Bicep Curl Repetition Counter is a practical demonstration of how a tilt sensor and basic digital ICs can be combined to build an exercise-counting prototype. The design brings together signal conditioning, timing, decade counting, BCD display decoding and magnitude comparison. Its central engineering challenge is ensuring that one complete curl produces exactly one count.

This report is a reconstructed description. The final pin connections, component values, measured performance and as-built circuit should be added only after checking the original hardware or reliable project records.

## 13. References

Consult the manufacturer datasheets for the exact IC variants used:

- 7414 / 74x14 Schmitt-trigger inverter.
- NE555 timer.
- 7490 / 74x90 decade counter.
- 7448 BCD-to-seven-segment decoder/driver.
- 7485 4-bit magnitude comparator.

Use the datasheet corresponding to the actual manufacturer and suffix printed on each IC.
