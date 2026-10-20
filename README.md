# Controls at User Facilities

A manuscript on how controls actually run at a neutron source or a synchrotron.

EPICS is the spine: records, IOCs, Channel Access, and PV Access. The book is the map around that layer. Naming, screens, alarms, the archive, motion, sensors, detectors, timing, the handoff to user data, protection, networks, and on-call operations.

The reader is a new controls engineer, or a beamline scientist who already knows that records exist and still cannot run a shift.

Two examples run through the whole book:

- A direct-geometry chopper spectrometer at a spallation source, in the SNS ARCS/SEQUOIA class.
- A photon beamline operated with Bluesky and ophyd, written from published NSLS-II and APS practice.

Accelerator physics, detector physics, and EPICS core development stay out. XFELs and muon sources get one paragraph in the opening chapter.

Published practice and cleaned examples only. Internal host names, tickets, and log excerpts do not belong here.

Start with [outline.md](outline.md).
