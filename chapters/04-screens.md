# 4. Screens

Status: outlined

## Job

Show that a display is a view of process variables, not a second control system. Phoebus is the client a new screen is written in. EDM and MEDM are the installed base a reader will still open.

## Covers

- The same PVs behind three display files. Phoebus uses `.bob`. EDM, the Extensible Display Manager, uses `.edl`. MEDM, the Motif Editor and Display Manager, uses `.adl`.
- What an operator does with a screen: open it, watch it, and write a setpoint. The record still enforces the limits.
- Phoebus Display Builder as the current usual editor. Data Browser belongs here only as the plot that can show a live value. The archived trace is chapter 6.
- EDM and MEDM as screens that already exist on a beamline. A facility does not redraw every display when it adopts Phoebus.
- Other display managers a reader will meet, named once: caQtDM and PyDM. They are the same job.

## Stays out

- A display-editor tutorial and widget-by-widget manuals.
- Site screen trees copied from a controls account.

## Draws on

- Phoebus: <https://www.controlsystemstudio.org/applications/>
- EPICS related software, user-interface tools: <https://docs.epics-controls.org/en/latest/software/epics-related-software.html>
- Chapter 3, because a screen completes names from the directory.
