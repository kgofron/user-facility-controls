# 6. Timing

Status: outlined

## Job

Treat timing as two different machines that both have to meet the detector.

## Covers

- Neutron case: a proton pulse, choppers that select energy, and a detector that timestamps events against that pulse. The chopper control system is often its own machine that EPICS supervises.
- Photon case: a storage-ring revolution clock and an event system that beamline hardware locks to. The beamline consumes accelerator timing. It does not operate the ring.
- What fails when timing is wrong: a dataset that looks complete and is not sortable.
- Chapter 7 uses this time base twice: neutron event timestamps, and time-of-flight histograms on a Serval pixel detector.

## Stays out

- Chopper physics and lattice physics.
- Event-system register maps.

## Draws on

- A published description of SNS chopper control for the locked spectrometer.
- A published description of the NSLS-II or APS event timing system, written as the interface a beamline sees.
