# Voron 2.4 R2 Klipper Configuration

## 📌 Important Documentation  
For CAN bus setup, troubleshooting, and configuration details, see:  
👉 **[CAN Bus Setup & Troubleshooting](docs/CanBus.MD)**

This repository contains the complete [Klipper](https://www.klipper3d.org/) configuration for a Voron 2.4 R2 350mm 3D printer, running on a BigTreeTech Octopus V1 mainboard, BIGTREETECH EBBCan (SB2209) toolhead board and a BTT CB1. It includes advanced features such as sensorless homing, adaptive meshing and purging (KAMP), timelapse, and more.

## Features

- **Voron 2.4 R2 350mm build**: CoreXY kinematics, quad gantry leveling, and bed mesh.
- **BigTreeTech Octopus V1**: Mainboard configuration with TMC2209 drivers.
- **BIGTREETECH EBBCan SB2209**: Toolhead board over CAN bus for extruder, fans, probe, and ADXL345 accelerometer.
- **Sensorless Homing**: Advanced macros for reliable sensorless homing on X and Y axes.
- **KAMP (Klipper Adaptive Meshing & Purging)**: Adaptive mesh and purge routines for optimal first layers and clean nozzle.
- **Filament Sensor**: Smart filament sensor with pause/resume macros.
- **Timelapse & Hyperlapse**: Automated camera control for print timelapses.
- **Macros**: Modular macro system for print start, pause, resume, cancel, filament change, LED control, and more.
- **Peripheral Management**: Crowsnest (camera streaming), Sonar (WiFi keepalive), and Mainsail/Fluidd compatibility.

## Directory Structure

```
KAMP/
feature_configs/
macros/
mcu_configs/
timelapse.cfg
moonraker.conf
printer.cfg
mainsail.cfg
KAMP_Settings.cfg
...
```

- **printer.cfg**: Main printer configuration, includes all other configs.
- **mcu_configs/**: Board-specific configs (Octopus, EBBCan, Pi MCU).
- **feature_configs/**: Optional features (e.g., sensorless homing).
- **macros/**: Modular macro files for various printer operations.
- **KAMP_Settings.cfg**: Settings for adaptive meshing and purging.
- **timelapse.cfg**: Timelapse macro definitions.
- **moonraker.conf**: Moonraker API server configuration.
- **crowsnest.conf, sonar.conf**: Camera and WiFi keepalive configs.

## Getting Started

1. **Clone this repository** to your Klipper configuration directory (usually `~/printer_data/config`).
2. **Review and update** the following files for your hardware:
   - [`printer.cfg`](printer.cfg)
   - [`mcu_configs/ebb_sb2209.cfg`](mcu_configs/ebb_sb2209.cfg)
   - [`mcu_configs/btt_pi_mcu.cfg`](mcu_configs/btt_pi_mcu.cfg)
3. **Check MCU serials and CAN UUIDs** in `[mcu]` and `[mcu EBBCan]` sections.
4. **Customize macros** as needed in the `macros/` directory.
5. **Enable/disable features** by commenting/uncommenting `[include ...]` lines in `printer.cfg` and `KAMP_Settings.cfg`.
6. **Restart Klipper** and verify operation via your web interface (Mainsail/Fluidd).

## Advanced Features

- **KAMP (Adaptive Meshing & Purging)**: See [`KAMP_Settings.cfg`](KAMP_Settings.cfg) for options.
- **Sensorless Homing**: Enable via [`feature_configs/sensorless_homing.cfg`](feature_configs/sensorless_homing.cfg).
- **Timelapse**: Configure in [`timelapse.cfg`](timelapse.cfg) and ensure camera is set up in [`crowsnest.conf`](crowsnest.conf).
- **Filament Sensor**: Configured in [`mcu_configs/btt_pi_mcu.cfg`](mcu_configs/btt_pi_mcu.cfg).

## Macros

Macros are organized in [`macros/macros_master.cfg`](macros/macros_master.cfg) and included from the `macros/macros_in_here/` directory. Key macros include:

- `PRINT_START`, `PRINT_END`
- `PAUSE`, `RESUME`, `CANCEL_PRINT`
- `FILAMENT_CHANGE`
- `PARK`, `G32` (quad gantry leveling)
- LED and display control

## Credits

- [Voron Design](https://vorondesign.com/)
- [Klipper](https://www.klipper3d.org/)
- [Mainsail](https://github.com/mainsail-crew/mainsail)
- [KAMP](https://github.com/kyleisah/Klipper-Adaptive-Meshing-Purging)
- [Crowsnest](https://github.com/mainsail-crew/crowsnest)
- [Sonar](https://github.com/mainsail-crew/sonar)

## License

This configuration is provided under the MIT License. See [LICENSE](LICENSE) for details.

---

**Note:** Always review and test configuration changes carefully. Incorrect settings may cause hardware