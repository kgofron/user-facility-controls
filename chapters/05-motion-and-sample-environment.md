# 5. Motion and sample environment

Status: outlined

## Job

Show two instrument systems that are mostly EPICS motors and temperatures, and the pieces that are not.

## Covers

- Single-axis motion through the motor record: slits, apertures, and sample positioners on both example instruments.
- Coordinated motion only far enough to show why a diffractometer is more than six motor records.
- Sample environment as its own service: cryostats, heaters, and the loops that hold a setpoint. Name SECoP where a facility uses it beside EPICS.
- What the user actually asks for during a shift: a temperature, a position, and a scan that will wait for both.

## Stays out

- Control theory and PID tuning recipes.
- Vendor motor-controller manuals.

## Draws on

- Public motor-record and synApps documentation.
- A published description of sample environment on the locked neutron instrument, added when that example is chosen.
