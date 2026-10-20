# 5. Motion and sample environment

Status: outlined

## Job

Show the two instrument subject areas that are mostly motors and sensors, and the pieces that are not plain records.

## Covers

- Single-axis motion through the motor record: slits, apertures, and sample positioners on both example instruments.
- Coordinated motion only far enough to show why a diffractometer is more than six motor records. The worked example is ioc-hkl: an EPICS layer that turns motor positions into reciprocal-space HKL using the hkl library. Name hklpy as the Bluesky counterpart, then stop.
- Sensors and sample environment as their own service: cryostats, heaters, vacuum, and the loops that hold a setpoint. Name SECoP where a facility uses it beside EPICS. This stays a section of this chapter, not a separate chapter.
- What the user actually asks for during a shift: a temperature, a position, and a scan that will wait for both.

## Stays out

- Crystallography, orientation refinement, and UB-matrix recipes.
- Control theory and PID tuning recipes.
- Vendor motor-controller manuals.

## Draws on

- Public motor-record and synApps documentation.
- ioc-hkl: <https://github.com/hkl-projects/ioc-hkl>
- hklpy: <https://github.com/bluesky/hklpy>
- A published description of sample environment on the locked neutron instrument, added when that example is chosen.
