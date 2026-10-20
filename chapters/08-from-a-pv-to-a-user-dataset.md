# 8. From a PV to a user dataset

Status: outlined

## Job

Follow one user run from the PVs that describe the instrument to the file or catalog the user analyzes.

## Covers

- The shared job on both paths: identity of the experiment, a start and a stop, the instrument state during the run, and a dataset.
- Neutron path: run control, event data, and NeXus. Use the locked chopper spectrometer.
- Photon path: Bluesky plans, ophyd devices over EPICS, and a databroker. The area-detector pipeline is chapter 7. This chapter starts from the NDArray or the file that pipeline already produced.
- Where a PV list enters the dataset, and where it stays in the control system.

## Stays out

- Reduction and analysis.
- NeXus application definitions beyond what the reader needs to see the handoff.
- Detector physics, and a second tour of areaDetector.

## Draws on

- Chapter 7 for the detector path.
- Bluesky and ophyd documentation.
- Public NeXus manual and public SNS data-path papers, added to [sources/reading-list.md](../sources/reading-list.md) when drafting starts.
