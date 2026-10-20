# 11. From a PV to a user dataset

Status: outlined

## Job

Follow one user run from the PVs that describe the instrument to the file or catalog the user analyzes.

## Covers

- The shared job on both paths: identity of the experiment, a start and a stop, the instrument state during the run, and a dataset.
- Neutron path, as two tools rather than one. The Scan Server sequences the instrument: a client submits a scan of set, wait, and loop commands, and the server runs that queue against process variables, with pause, resume, and abort. Run control is the boundary of a numbered acquisition: start, stop, and the rule that pauses counting when a watched value leaves a range. Event data and NeXus are what that run files. Use the locked chopper spectrometer.
- Photon path: Bluesky plans, ophyd devices over EPICS, and a databroker. One Bluesky run is both the sequence and the dataset boundary. The area-detector pipeline is chapter 10. This chapter starts from the NDArray or the file that pipeline already produced.
- The comparison, kept short. The Scan Server and a Bluesky plan are the same class: they order moves and waits above EPICS. Run control and a Bluesky run document are the same class: they say when a measurement starts and stops. Bluesky puts both classes in the RunEngine. SNS keeps them apart, because the scan can change while the run, the event stream, and the NeXus file stay the facility's record of what the user took.
- Where a PV list enters the dataset, and where it stays in the control system.

## Stays out

- Reduction and analysis.
- A command-by-command manual for the Scan Server, and a plan-by-plan manual for Bluesky.
- NeXus application definitions beyond what the reader needs to see the handoff.
- Detector physics, and a second tour of areaDetector.

## Draws on

- Chapter 10 for the detector path.
- Bluesky and ophyd documentation.
- Public NeXus manual and public SNS data-path papers, added to [sources/reading-list.md](../sources/reading-list.md) when drafting starts.
