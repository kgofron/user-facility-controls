# 7. From a PV to a user dataset

Status: outlined

## Job

Follow one user run from the PVs that describe the instrument to the file or catalog the user analyzes.

## Covers

- The shared job on both paths: identity of the experiment, a start and a stop, the instrument state during the run, and a dataset.
- Neutron path: run control, event data, and NeXus. Use the locked chopper spectrometer.
- Photon path: Bluesky plans, ophyd devices over EPICS, area detectors, and a databroker. Use the locked beamline.
- Where a PV list enters the dataset, and where it stays in the control system.

## Stays out

- Reduction and analysis.
- NeXus application definitions beyond what the reader needs to see the handoff.
- Detector physics.

## Draws on

- Bluesky and ophyd documentation.
- areaDetector documentation.
- Public NeXus manual and public SNS data-path papers, added to [sources/reading-list.md](../sources/reading-list.md) when drafting starts.
