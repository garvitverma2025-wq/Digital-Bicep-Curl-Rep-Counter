# Component Reference

This page summarises the intended role of each known component in the Digital Bicep Curl Rep Counter. Check the exact manufacturer datasheet and IC suffix before wiring or powering the circuit.

## Tilt sensor

**Purpose:** Detects a change in orientation of the dumbbell or moving assembly.

**Integration notes:**
- Secure the sensor so it cannot shift during exercise.
- Identify its output type and required pull-up or pull-down arrangement.
- Test the sensor independently before connecting it to the logic stages.
- Confirm which orientation is treated as active.

## 7414 Schmitt-trigger inverter

**Purpose:** Provides an inverting logic stage with Schmitt-trigger input characteristics. Hysteresis helps clean up slowly changing or noisy signals.

**Integration notes:**
- Confirm the supply and logic-level requirements for the exact IC.
- Check the sensor's voltage levels against the IC input limits.
- Remember that the output is inverted.
- Do not assume that the 7414 alone guarantees one count per full exercise cycle.

## NE555 timer

**Purpose:** Used as a timing or pulse-generation stage in the project.

**Integration notes:**
- Confirm whether the actual circuit uses monostable, astable or another configuration.
- Record the resistor and capacitor values from the built circuit.
- Check the output pulse width and ensure the counter sees one clean event per intended repetition.
- Add supply decoupling as recommended by the datasheet.

## 7490 decade counter

**Purpose:** Counts pulses in a decade sequence and provides BCD-related outputs.

**Integration notes:**
- Verify the required clock input and reset wiring from the exact datasheet.
- Check the intended count sequence before connecting the display.
- Confirm how the counter is cascaded if more than one digit is used.

## 7448 BCD-to-seven-segment decoder/driver

**Purpose:** Converts a BCD input into segment-control outputs for a seven-segment display.

**Integration notes:**
- Confirm display compatibility and output polarity for the exact 7448 variant.
- Include current-limiting resistors where required by the display and IC design.
- Verify segment pin mapping before powering the circuit.

## 7485 4-bit magnitude comparator

**Purpose:** Compares two four-bit binary values and indicates whether one is less than, equal to or greater than the other.

**Integration notes:**
- Confirm the A and B input ordering and the cascade input configuration.
- A single 7485 compares only four bits.
- Ensure the counter value and preset target are encoded in the same representation.

## Seven-segment display

**Purpose:** Provides a visible numerical count.

**Integration notes:**
- Identify whether the display is common-anode or common-cathode.
- Match the display to the decoder/driver output requirements.
- Confirm segment pinout and use suitable current limiting.

## Power supply and passive components

Use the supply voltage specified by each exact IC datasheet. Check resistor and capacitor values against the actual schematic. Never infer component values from a generic example circuit.
