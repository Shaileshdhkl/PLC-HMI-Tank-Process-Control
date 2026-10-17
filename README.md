# PLC-HMI Tank Process Control System

Shailesh Dhakal | Electrical Engineering | University of South Florida

An integrated process-control project using a CompactLogix 5380 PLC, PanelView 5510 HMI, and PowerFlex 525 VFD. The tank is modeled mathematically, while the PLC and operator interface manage commands, process values, warnings, faults, and permitted setpoint changes. Motor frequency represents the simulated filling rate.

## Engineering Highlights

- Modular ladder logic for Start/Stop control, warnings, latched faults, reset handling, status, and indication outputs.
- A tank-level model executed in a 100-ms periodic task, with values constrained between 0 and 100.
- VFD command generation, command limiting, and removal of the frequency command when stopped or faulted.
- HMI Home and Control screens with controller-tag bindings, momentary commands, numeric setpoints, tank graphics, and navigation.
- A trend popup for fill-speed and depletion-rate setpoints.
- Guest, Operator, and Administrator access, including an Administrator-only depletion-rate input.

## Implementation

I implemented the PLC control routines and tank model, configured the HMI screens and controller-tag bindings, and integrated setpoint handling, status displays, trend configuration, and user-role restrictions. I documented the logic and recorded online high-fault behavior in the project report.

## System Architecture

HMI commands and setpoints -> CompactLogix control logic -> VFD command and indication outputs

100-ms tank model -> Level monitoring -> Warning/fault logic -> HMI status and graphics

The tank model uses filling and depletion setpoints with scaling coefficients and a 0.1-second time step. A reset restores the simulated level to 50 and clears the latched system fault.

## Warning and Fault Thresholds

| Condition | Simulated tank level |
| --- | --- |
| High warning | 80 to less than 95 |
| High fault | 95 or greater |
| Low warning | Greater than 5 to 20 |
| Low fault | 5 or less |

## Documented Verification

The report records the controller online in REM RUN mode. At approximately 95.007 tank level, the high-fault condition became active, the system fault latched, the status changed to Faulted, and the fault-indication logic became active.

HMI screenshots document the screen layout, tag-related configuration, trend popup, and Administrator-only depletion-rate expression. These configuration records are distinct from the observed online fault test. The report does not include a full measurement log for every physical indicator or operating condition.

## Tools and Hardware

- Studio 5000 Logix Designer
- Studio 5000 View Designer
- CompactLogix 5380 PLC
- PanelView 5510 HMI
- PowerFlex 525 VFD
- Ladder Logic

## Documentation

The project report, PLC_HMI_Tank_Process_Control_Project_Report.docx, has been prepared and is pending upload to this repository. It includes system architecture, a process flow diagram, ladder screenshots, HMI configuration, verification results, and engineering analysis.

## Project Scope

The tank feedback is simulated rather than measured from a physical tank. Extending the project to a real process would require tank-level instrumentation, pumps, and consideration of process dynamics and measurement noise.
