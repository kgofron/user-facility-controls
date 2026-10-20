# 2. EPICS as the common layer

Status: outlined

## Job

Give the reader enough EPICS to follow the rest of the book: records, IOCs, Channel Access, and PV Access.

## Covers

- A record as a named unit of behavior, an IOC as the process that serves it, and a PV as the name on the wire. Field lists and record types stay in the IOC Component Reference, which is the current name of the old Record Reference Manual.
- Channel Access for search, read, write, and monitor.
- PV Access as the structured protocol facilities add beside Channel Access, not a flag day.
- Soft IOCs, VME and other embedded IOCs, and servers that speak the protocol without being a standard IOC. LabVIEW belongs in that last set, because later chapters depend on it.
- Mixed Base versions as a fact of life. SNS still runs IOCs as old as Base 3.14.8.2 next to newer ones. Cite the published paper rather than a lab inventory.

## Stays out

- EPICS core development, database internals, and how to write a device support module.
- A substitute for the Application Developer's Guide or the IOC Component Reference. Point at them and move on.

## Draws on

- Application Developer's Guide: <https://docs.epics-controls.org/en/latest/appdevguide/AppDevGuide.html>
- IOC Component Reference: <https://docs.epics-controls.org/projects/base/en/latest/ComponentReference.html>
- Base 3.16.2 Application Developer's Guide, for an IOC still on that generation: <https://epics.anl.gov/base/R3-16/2-docs/AppDevGuide/AppDevGuide.html>
- Vodopivec and Cashion, ICALEPCS 2025, TUBR004, for the mixed-version fact.
