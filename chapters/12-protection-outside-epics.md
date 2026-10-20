# 12. Protection systems that are deliberately not EPICS

Status: outlined

## Job

Separate the three protection layers so a reader stops expecting EPICS to be the safety system.

## Covers

- Personnel safety: protects people, hardwired or PLC-based, authoritative whether or not EPICS is up.
- Equipment and machine protection: protects hardware, including shutters, choppers, and beamline components. Still outside the record database.
- Software limits inside EPICS: useful, bypassable, and not a substitute for the two layers above.
- What an EPICS screen is allowed to show about those systems: status, not authority.

## Stays out

- Interlock equations, wiring, network segmentation, and anything that is not already published.
- A design manual for a personnel safety system.

## Draws on

- Published facility descriptions of personnel safety and equipment protection, at the level of roles.
- Chapter 1 for the boundary this chapter pays off.

Write this chapter last among the technical chapters, and read it again before any push.
