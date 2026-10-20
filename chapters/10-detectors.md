# 10. Detectors

Status: outlined

## Job

Show how a facility controls a detector. Detector physics stays out. The subject is the control and data path: configure, acquire, and hand frames or events to the next chapter.

## Covers

- areaDetector as the common photon-side layer: a driver, an NDArray, plugins, and a file writer. Link the project, and do not reproduce its manual.
- Two detector shapes on the two example instruments. The photon beamline uses an area detector. The chopper spectrometer uses an event-mode detector that timestamps neutrons against the pulse from chapter 9. Both are detectors. Only one of them is a camera.
- ADTimePix3, also called ADServal, as the worked driver. One areaDetector driver covers a Serval family: TimePix3 and Medipix3, with TimePix4 planned. Configuration and preview go over the vendor's REST and TCP streams. Time-of-flight histograms are the point where this driver meets chapter 9.
- The vendor service is not the IOC. Serval runs as its own process. Chapter 14 shows how EPICS starts and watches that process.

## Stays out

- A driver-writing tutorial, chip geometry, and pixel masks beyond what the example needs.
- Detector physics and data reduction.
- A second explanation of how frames become a user dataset. That is chapter 11.

## Draws on

- areaDetector: <https://github.com/areaDetector/areaDetector>
- ADTimePix3 (ADServal): <https://github.com/areaDetector/ADTimePix3>
- areaDetector documentation: <https://areadetector.github.io/areaDetector/index.html>
