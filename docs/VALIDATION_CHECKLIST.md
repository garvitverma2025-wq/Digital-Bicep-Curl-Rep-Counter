# Hardware Validation Checklist

Use this checklist when the original hardware is available again. It is intentionally left as a checklist rather than claiming tests were passed.

## Before powering the circuit

- [ ] Photograph the complete circuit from above.
- [ ] Photograph each IC marking so exact part numbers can be read.
- [ ] Record the tilt sensor part number and pinout.
- [ ] Trace and document the actual wiring.
- [ ] Record all resistor and capacitor values.
- [ ] Identify the seven-segment display type.
- [ ] Check power and ground connections against the datasheets.
- [ ] Check for shorts between supply rails.

## Functional tests

- [ ] Verify the tilt sensor output in both orientations.
- [ ] Verify the 7414 input and output logic states.
- [ ] Verify the NE555 configuration and output waveform.
- [ ] Verify the 7490 count sequence using known input pulses.
- [ ] Verify that the 7448 display output matches the BCD input.
- [ ] Verify the 7485 less-than, equal-to and greater-than outputs.
- [ ] Perform one complete curl and confirm exactly one count.
- [ ] Repeat for at least ten complete curls and record any missed or extra counts.
- [ ] Test the target comparison, if connected in the final build.

## Add evidence to the repository

Recommended files:

- `images/overall-build.jpg` — complete hardware.
- `images/sensor-mounting.jpg` — tilt sensor placement.
- `images/display-count.jpg` — display during operation.
- `images/circuit-closeup.jpg` — readable IC and wiring close-up.
- `images/logic-diagram.png` — verified circuit or block diagram.
- `docs/test-results.md` — actual observations and measurements.

Only add photos and results from the real build. Do not label a conceptual diagram as the final tested circuit.
