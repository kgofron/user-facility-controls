# Outline

Working title: **Controls at User Facilities**

Subtitle: *How EPICS sits among timing, data, sample environment, protection, and operations.*

Repository: `user-facility-controls`

Voice: an SNS controls engineer comparing facilities. APS and NSLS-II come from their published practice. SNS chapters may use the author's own work when it is already public.

## Audience

A new controls engineer, or a beamline scientist who can find a record and still cannot run a shift.

## Scope

In:

- What a user facility is controlling, and where the safety boundary sits.
- EPICS as the common layer.
- Names and directories.
- Screens, alarms, the archive, and the logbook.
- Motion, with reciprocal-space motion as an example, and sensors as sample environment.
- Timing, as two cases: neutron choppers and a storage-ring timing system.
- Detectors: areaDetector as the common layer, plus the event-mode neutron case.
- The handoff from a PV to a user dataset.
- Protection that stays outside EPICS.
- Networks, deployment, and on-call work.

Out:

- Accelerator physics, including fast orbit feedback except as a boundary the beamline consumes.
- Detector physics. Detector control is chapter 10. The handoff from frames or events to a dataset is chapter 11.
- EPICS core development.
- XFEL and muon sources, beyond one paragraph in chapter 1.
- Internal host names, tickets, log excerpts, interlock equations, and network segmentation.

## Examples held constant

Pick these before drafting chapter 1, then use them in every later chapter.

| Path | Example | Why this one |
| --- | --- | --- |
| Neutron | A direct-geometry chopper spectrometer, SNS ARCS/SEQUOIA class | Choppers, sample environment, event data, and NeXus in one instrument |
| Photon | One published NSLS-II or APS beamline that runs Bluesky and ophyd | The photon path above EPICS, not only a different file format |

Describe them as classes from published papers and manuals.

## Worked tools

These are examples inside a chapter, not chapters of their own. Link the public repository, not a local install path.

| Tool | Chapter | Role |
| --- | --- | --- |
| [ioc-hkl](https://github.com/hkl-projects/ioc-hkl) | 8 | Reciprocal-space motion. hklpy is the Bluesky counterpart, named once. |
| [areaDetector](https://github.com/areaDetector/areaDetector) | 10 | The common detector layer: driver, NDArray, plugins, file writer. |
| [ADTimePix3](https://github.com/areaDetector/ADTimePix3) | 10 | One Serval-family driver, TimePix3 and Medipix3, inside that layer. |
| [systemdIOC](https://github.com/kgofron/systemdIOC) | 14 | EPICS control of a systemd service. The motivating case is Serval, so chapter 10 points here. |

## Chapters

| | File | Job |
| --- | --- | --- |
| 1 | [chapters/01-what-the-facility-controls.md](chapters/01-what-the-facility-controls.md) | What is being controlled, and where the safety boundary sits |
| 2 | [chapters/02-epics-as-the-common-layer.md](chapters/02-epics-as-the-common-layer.md) | Records, IOCs, Channel Access, and PV Access |
| 3 | [chapters/03-names-directories-finding-a-pv.md](chapters/03-names-directories-finding-a-pv.md) | Channel Finder, recsync, and finding a PV |
| 4 | [chapters/04-screens.md](chapters/04-screens.md) | Phoebus, EDM, and MEDM |
| 5 | [chapters/05-alarms.md](chapters/05-alarms.md) | Alarm Handler and the Phoebus alarm server |
| 6 | [chapters/06-archiver-appliance.md](chapters/06-archiver-appliance.md) | Archiver Appliance, and the older Channel Archiver |
| 7 | [chapters/07-logbooks.md](chapters/07-logbooks.md) | Olog, ELOG, and other logbooks |
| 8 | [chapters/08-motion-and-sample-environment.md](chapters/08-motion-and-sample-environment.md) | Motion, reciprocal space, and sensors |
| 9 | [chapters/09-timing.md](chapters/09-timing.md) | Choppers and storage-ring timing |
| 10 | [chapters/10-detectors.md](chapters/10-detectors.md) | areaDetector, Serval, and neutron event mode |
| 11 | [chapters/11-from-a-pv-to-a-user-dataset.md](chapters/11-from-a-pv-to-a-user-dataset.md) | Scan Server and run control beside Bluesky, then the dataset |
| 12 | [chapters/12-protection-outside-epics.md](chapters/12-protection-outside-epics.md) | Personnel safety, equipment protection, software limits |
| 13 | [chapters/13-networks-and-the-broadcast-problem.md](chapters/13-networks-and-the-broadcast-problem.md) | Gateways, name servers, and PVmapper |
| 14 | [chapters/14-deployment-change-on-call.md](chapters/14-deployment-change-on-call.md) | Deployment, systemd services, and on-call |

## Companion note

[channelfinder-pvmapper](https://github.com/kgofron/channelfinder-pvmapper) is a tool comparison, not a chapter. Chapter 3 takes Channel Finder and recsync. Chapter 13 takes PVmapper, the classic CA name server, and CA Gateway. `cainfo` asks the same host question as PVmapper and then forgets the answer; it belongs with on-call troubleshooting in chapter 14. `cfNameserver` is the one-line bridge: a pvAccess name server backed by the Channel Finder catalog.

## Next

1. Lock the two example instruments from published sources.
2. Finish the gateway boundary in chapter 13. The host-finding comparison, including `cainfo` and PVmapper, is drafted. The comparison note and Vodopivec and Cashion, ICALEPCS 2025, TUBR004, carry the public facts.
3. Draft chapter 10 from the public areaDetector and ADTimePix3 repositories, then chapter 11: neutron run, event data, and NeXus beside Bluesky and ophyd.
4. Add glossary entries as each chapter is drafted.
5. Sensitivity pass on chapters 12 and 13 before any push. Roles and patterns only.
