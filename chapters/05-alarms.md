# 5. Alarms

Status: outlined

## Job

Show an alarm as a filtered stream, not as every record that happens to be in alarm. The operator needs a tree, an acknowledgement, and guidance. The classic tool for that tree is the Alarm Handler. A current Phoebus control room uses the Phoebus alarm server.

## Covers

- Why a record's alarm fields are not yet an alarm system. Something has to group them, keep them on screen, and record that an operator saw them.
- The Alarm Handler (ALH): a Motif client that watches record alarm state over Channel Access, shows a hierarchy, and lets the operator acknowledge. Its configuration is a file the facility maintains.
- The Phoebus alarm server and Alarm Table: the system an operator meets now. The table shows current alarms. The alarm log shows past alarm events. BEAST is the deprecated predecessor inside older Control System Studio.
- The tree is built from names and tags. Chapter 3 is how a site finds the channels that belong in it.
- An alarm is not a protection system. Chapter 12 is the boundary. An alarm tells a person. A personnel safety system does not ask for an acknowledgement.

## Stays out

- How to write an ALH configuration file or a Phoebus alarm tree.
- Alarm philosophy checklists and site alarm-rate targets.

## Draws on

- Alarm Handler User's Guide: <https://epics.anl.gov/EpicsDocumentation/ExtensionsManuals/AlarmHandler/alhUserGuide-1.2.35/ALHUserGuide.html>
- Phoebus Alarm Table and Alarm Log: <https://www.controlsystemstudio.org/applications/>
- Phoebus alarm server: <https://control-system-studio.readthedocs.io/en/latest/services/alarm-server/doc/index.html>
