# Factory I/O Sorting by Height System

An industrial automation project that simulates a conveyor-based package sorting system using **Factory I/O**, **Siemens TIA Portal**, and a **Siemens S7-1200 PLC** programmed in **Ladder Logic (LAD)**.

> **Project status:** Simulation and PLC integration screenshots are included. Add the final PLC project export and demonstration video if you want them available in this repository.

---

## Project Overview

This project demonstrates an automated material-handling system in which packages move through a conveyor arrangement and are routed according to their detected height.

The Factory I/O scene contains an entry conveyor, a transfer section, left and right conveyor paths, sensors, and a control panel. The PLC program handles the start/stop and emergency-stop conditions, conveyor sequencing, and sorting/transfer operations.

## Software and Tools

- **Factory I/O** – 3D factory simulation
- **Siemens TIA Portal** – PLC programming and configuration
- **Siemens S7-1200** – PLC platform shown in the project
- **Siemens PLCSIM** – PLC simulation/connection (if used in the final setup)
- **Ladder Logic (LAD)** – PLC programming language

## System Layout

The simulated system includes:

- Entry conveyor
- Transfer conveyor/section
- Left and right conveyor paths
- Low-height and high-height sensors
- Package/pallet presence and position sensors
- Transfer actuators
- Operator control panel

## Working Principle

1. The operator selects the operating mode and starts the system.
2. The entry conveyor transports a package into the sensing/transfer area.
3. The height sensors detect whether the package is low or high.
4. The PLC processes the sensor signals and controls the conveyor and transfer outputs.
5. The transfer mechanism routes the package to the appropriate conveyor path.
6. Position/exit sensors provide feedback as the package moves through the system.
7. The sequence returns to its ready state for the next package.

> Confirm the exact destination assigned to high and low packages against your final PLC logic before publishing this description.

## Operator Control Panel

The Factory I/O control panel shown in the screenshots includes:

- Emergency Stop
- Start
- Stop
- Reset
- Counter display
- Manual / Auto selector

The emergency-stop function should be treated as a safety-related function in a real installation. A Factory I/O simulation and ordinary PLC logic alone do not establish a safety-rated implementation.

## PLC I/O Mapping

The following addresses are transcribed from the Factory I/O driver configuration screenshot. Verify them against the final TIA Portal tag table before relying on them.

### Digital Inputs

| Signal | PLC Address |
|---|---:|
| Start | `%I0.0` |
| Stop | `%I0.1` |
| Emergency stop | `%I0.2` |
| Low sensor | `%I0.3` |
| High sensor | `%I0.4` |
| Loaded | `%I0.5` |
| At right entry | `%I0.6` |
| At left entry | `%I0.7` |
| Pallet sensor | `%I1.0` |
| At right exit | `%I1.1` |
| At left exit | `%I1.2` |
| Reset | `%I1.3` |

### Digital Outputs

| Signal | PLC Address |
|---|---:|
| Transfer right | `%Q0.0` |
| Transfer left | `%Q0.1` |
| Conveyor right | `%Q0.2` |
| Conveyor left | `%Q0.3` |
| Load | `%Q0.4` |
| Conveyor entry | `%Q0.5` |
| Start light | `%Q0.6` |
| Stop light | `%Q0.7` |

The driver screenshot also shows additional output/word entries (including `%Q1.0`, `%Q1.1`, and `%QW30`). Their exact signal assignments should be confirmed from the complete driver mapping or TIA Portal tag table before adding them here.

## PLC Program

The available TIA Portal screenshot shows a state-handler block and networks related to fault-safe handling, emergency-stop handling, and the conveyor start sequence.

Add further screenshots and a short explanation of each network here once the complete ladder program is documented.

## Screenshots

Store image files in the `screenshots/` folder and use these filenames (or update the links to match your own filenames).

### Factory I/O – Conveyor System

![Factory I/O conveyor system](screenshots/01_factoryio_overview.png)

### TIA Portal – PLC Ladder Logic

![TIA Portal ladder logic](screenshots/02_tia_portal_ladder_logic.png)

### Factory I/O – Driver I/O Configuration

![Factory I/O driver configuration](screenshots/03_driver_io_mapping.png)

### Factory I/O – Operator Control Panel

![Factory I/O operator control panel](screenshots/04_operator_control_panel.png)

## Repository Structure

```text
Factory-IO-Sorting-by-Height/
├── README.md
├── documentation/
│   ├── system_overview.md
│   └── io_mapping.md
├── screenshots/
│   ├── 01_factoryio_overview.png
│   ├── 02_tia_portal_ladder_logic.png
│   ├── 03_driver_io_mapping.png
│   └── 04_operator_control_panel.png
├── tia_project/
│   └── (add your TIA Portal project archive here)
└── videos/
    └── (add your Factory I/O demonstration video here)
```

## How to Run

1. Open the TIA Portal project in a compatible TIA Portal version.
2. Check the PLC device configuration and tag addresses.
3. Open the Factory I/O scene.
4. Select/configure the Siemens S7-PLCSIM driver to match the PLC project.
5. Verify all input and output mappings.
6. Start the PLC simulation and Factory I/O scene.
7. Test normal operation, manual/automatic selection, reset, stop, and emergency-stop behaviour.

Exact steps may vary with the TIA Portal, PLCSIM, and Factory I/O versions used.

## Skills Demonstrated

- PLC programming using Ladder Logic
- Siemens S7-1200 configuration
- Factory I/O simulation
- Sensor and actuator integration
- Conveyor control and sequencing
- PLC–simulation communication
- Industrial automation troubleshooting

## Future Improvements

- Add a complete I/O/tag table with signal descriptions.
- Document each ladder-logic network.
- Include a system sequence or flowchart.
- Add a demonstration video.
- Add test cases for different package heights and stop/reset conditions.

---

## Author

Add your name, GitHub profile, and project date here.

## License

Choose a license before distributing the project files. If you do not intend to grant reuse rights, do not add a permissive license by default.
