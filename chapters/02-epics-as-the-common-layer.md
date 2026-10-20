# 2. EPICS as the common layer

Status: client-pair table drafted. The rest of the chapter is still an outline.

## Job

Give the reader enough EPICS to follow the rest of the book: records, IOCs, Channel Access, and PV Access.

## Covers

- A record as a named unit of behavior, an IOC as the process that serves it, and a PV as the name on the wire. Field lists and record types stay in the IOC Component Reference, which is the current name of the old Record Reference Manual.
- Channel Access for search, read, write, and monitor.
- PV Access as the structured protocol facilities add beside Channel Access. The command pairs are the table below.
- Soft IOCs, VME and other embedded IOCs, and servers that speak the protocol without being a standard IOC. LabVIEW belongs in that last set, because later chapters depend on it.
- Mixed Base versions as a fact of life. SNS still runs IOCs as old as Base 3.14.8.2 next to newer ones. Cite the published paper rather than a lab inventory.

## Two protocols, one Base

EPICS V4 is the old name of the PV Access work. EPICS 7 is the release that ships PV Access beside Channel Access in the same Base. A facility runs both. The version number is not a separate control system, and it is not a separate chapter.

The commands come in pairs. `pvinfo` prints the server and the structure of the value. `cainfo` prints the host, the native type, the element count, and the access rights. PVXS is the newer C++ implementation of PV Access. Its documentation tells day-to-day users to keep typing the pvAccess commands. The `pvx` forms are the same jobs for someone building against that library. "PV Info" in chapter 3 is the Channel Finder web page, not the `pvinfo` command.

| Job | Channel Access | PV Access | PVXS |
| --- | --- | --- | --- |
| One name: where it is, and what shape the value has | `cainfo` | `pvinfo` | `pvxinfo` |
| Read | `caget` | `pvget` | `pvxget` |
| Write | `caput` | `pvput` | `pvxput` |
| Monitor | `camonitor` | `pvmonitor` | `pvxmonitor` |
| List servers already visible |  | `pvlist` | `pvxlist` |
| Watch search traffic | caSnooper |  | `pvxvct` |

`pvlist` has no Channel Access twin. caSnooper's closest PV Access cousin is `pvxvct`, which watches search and beacon traffic. Chapter 13 is where those search-path tools are used. This table is only the names.

## Stays out

- EPICS core development, database internals, and how to write a device support module.
- A substitute for the Application Developer's Guide or the IOC Component Reference. Point at them and move on.
- A protocol specification for Channel Access or PV Access, and a second tour of normative types.

## Draws on

- Application Developer's Guide: <https://docs.epics-controls.org/en/latest/appdevguide/AppDevGuide.html>
- IOC Component Reference: <https://docs.epics-controls.org/projects/base/en/latest/ComponentReference.html>
- Base 3.16.2 Application Developer's Guide, for an IOC still on that generation: <https://epics.anl.gov/base/R3-16/2-docs/AppDevGuide/AppDevGuide.html>
- PV Access command-line tools: <https://docs.epics-controls.org/en/latest/pv-access/overview.html>
- PVXS command-line tools: <https://epics-base.github.io/pvxs/cli.html>
- Vodopivec and Cashion, ICALEPCS 2025, TUBR004, for the mixed-version fact.
