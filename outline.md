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
- Screens, alarms, and the archive.
- Motion and sample environment.
- Timing, as two cases: neutron choppers and a storage-ring timing system.
- The handoff from a PV to a user dataset.
- Protection that stays outside EPICS.
- Networks, deployment, and on-call work.

Out:

- Accelerator physics, including fast orbit feedback except as a boundary the beamline consumes.
- Detector physics. Detector control and the DAQ handoff stay in.
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

## Chapters

| | File | Job |
| --- | --- | --- |
| 1 | [chapters/01-what-the-facility-controls.md](chapters/01-what-the-facility-controls.md) | What is being controlled, and where the safety boundary sits |
| 2 | [chapters/02-epics-as-the-common-layer.md](chapters/02-epics-as-the-common-layer.md) | Records, IOCs, Channel Access, and PV Access |
| 3 | [chapters/03-names-directories-finding-a-pv.md](chapters/03-names-directories-finding-a-pv.md) | Channel Finder, recsync, and finding a PV |
| 4 | [chapters/04-screens-alarms-archive.md](chapters/04-screens-alarms-archive.md) | Screens, alarms, and the archive |
| 5 | [chapters/05-motion-and-sample-environment.md](chapters/05-motion-and-sample-environment.md) | Motion and sample environment |
| 6 | [chapters/06-timing.md](chapters/06-timing.md) | Choppers and storage-ring timing |
| 7 | [chapters/07-from-a-pv-to-a-user-dataset.md](chapters/07-from-a-pv-to-a-user-dataset.md) | Run control, event data, NeXus, and Bluesky |
| 8 | [chapters/08-protection-outside-epics.md](chapters/08-protection-outside-epics.md) | Personnel safety, equipment protection, software limits |
| 9 | [chapters/09-networks-and-the-broadcast-problem.md](chapters/09-networks-and-the-broadcast-problem.md) | Gateways, name servers, and PVmapper |
| 10 | [chapters/10-deployment-change-on-call.md](chapters/10-deployment-change-on-call.md) | Deployment, change, and on-call |

## Companion note

[channelfinder-pvmapper](https://github.com/kgofron/channelfinder-pvmapper) is a tool comparison, not a chapter. Chapter 3 takes Channel Finder and recsync. Chapter 9 takes PVmapper, the classic CA name server, and CA Gateway. `cfNameserver` is the one-line bridge: a pvAccess name server backed by the Channel Finder catalog.

## Next

1. Lock the two example instruments from published sources.
2. Draft chapter 9, then chapter 3. The comparison note and Vodopivec and Cashion, ICALEPCS 2025, TUBR004, already carry the public facts.
3. Draft chapter 7 next: neutron run, event data, and NeXus beside Bluesky, ophyd, and area detectors.
4. Add glossary entries as each chapter is drafted.
5. Sensitivity pass on chapters 8 and 9 before any push. Roles and patterns only.
