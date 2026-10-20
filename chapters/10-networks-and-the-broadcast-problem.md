# 10. Networks and the broadcast problem

Status: outlined

## Job

Explain why a large Channel Access network needs a gateway or a name server, and why those are different fixes.

## Covers

- How a client finds a PV: UDP search, and what happens when thousands of clients search for names that are gone.
- CA Gateway as the usual boundary between networks, and the remaining path where a public-side client still causes private-side searches.
- The classic CA name server, which wants a preloaded PV-to-host list.
- PVmapper: no IOC change, in-memory cache, Channel Access only. The published SNS result: on the order of a million PVs, search traffic down by about an order of magnitude, and a second instance so the service is not a single point of failure. `cainfo` prints the host for one name and then forgets it. PVmapper is the service that keeps that answer for every client. The probe itself is chapter 11.
- Why Channel Finder was set aside for that particular problem: recsync does not cover every server SNS still runs.
- cfNameserver as the pvAccess counterpart, younger, and dependent on the catalog in chapter 3.

## Stays out

- A second copy of the Channel Finder catalog. Point back to chapter 3.
- Host names, addresses, and a procedure for building the service.

## Draws on

- Companion note, search-path half: <https://github.com/kgofron/channelfinder-pvmapper>
- Vodopivec and Cashion, ICALEPCS 2025, TUBR004. <https://proceedings.jacow.org/icalepcs2025/pdf/TUBR004.pdf>
- PVmapper: <https://github.com/klemenv/PVmapper>
