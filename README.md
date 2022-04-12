# LHR2021
This is the repository for the files associated with the paper "DIY Liquid Handling Robots for Integrated STEM Education and Life-Science Research".

This includes the following:
1. Hardware documentation:
    - Parts list
    - CAD source designs for mechanical parts
    - Laser cutting fabrication files (5 sheets)
    - Fabrication files for 3D printed parts
    - Electronic circuit schematic diagrams and CAD files
    - Assembly instructions
2. Software:
    - Low-level control software for Arduino
    - Python API and tools for tuning and calibration
    - Snap4Arduino visual programming environment

## Contents

The `hardware/` directory of this repository contains fabrication files and documentation for all hardware for the three-axis robot. CAD source designs for the mechanical components and subassemblies of the robot can be found in an associated [Onshape project](https://cad.onshape.com/documents/6f3ff9e60612f07463807b51/w/7c9831bb106114d48918156b/e/005c0d1900650c2e45e341be?renderMode=0&uiState=6254cec2aa34676ff2f642a7), which is made public for copying and exporting. These source designs were exported to create the cut patterns in `hardware/laser_cut_CAD_files/` and the 3D printing files in `hardware/3d_printed_CAD_files/`.

Source code and overview-level documentation of all software can be found at the associated repository [github.com/ethanjli/liquid-handling-robotics](https://github.com/ethanjli/liquid-handling-robotics).

## Usage

This hardware was developed and tested until October 2018 and is not currently maintained or supported. Troubleshooting and extensive technical skills will be needed to replicate the hardware design provided in this repository, requiring deep familiarity with laser cutting, 3-D printing, assembly of simple printed circuit boards, and circuit prototyping.

### Mechanical Fabrication

Laser-cut parts, collected in the `hardware/laser_cut_CAD_files/annotated_laser_cutting_pdf_files.zip` file, are designed for 1/8-inch thick acrylic plates. Due to kerf and thickness variations among laser cutters and acrylic plates, the laser cutting patterns may need to be manually re-exported from the Onshape CAD source project after modifying the `kerfAdjustment` FeatureScript variable in the [`Design Parameters/Acrylic` tab](https://cad.onshape.com/documents/6f3ff9e60612f07463807b51/w/7c9831bb106114d48918156b/e/27868389b7af3fd50301f4c9) of the project.

Two units of the magnet hub, used in the x- and y-axis linear actuators of the robot, will need to be 3D printed using the `hardware/3d_printed_CAD_files/Magnet Hub (in).stl` file or the `hardware/3d_printed_CAD_files/Magnet Hub (mm).stl` file, depending on the length units used by the 3D printer. 

### Mechanical Assembly

Mechanical assembly can be performed following the photographs and notes in the `hardware/assembly_instructions/LHR Assembly of Laser Cut Parts.pdf` file.

A 8mm x 2.50mm magnet, listed in the bill of materials, will need to be inserted into each 3D-printed magnet hub, and a magnet hub should be press-fitted to the D-shaped output shaft of the motor for each of the x- and y-axis linear actuators. A magnetic angle sensor printed circuit board (described below) should then be mounted to the linear actuator so that the angle sensor contacts the magnet.

### Circuit Assembly

The printed circuit board for the magnetic angle sensor, used in the x- and y-axis linear actuators of the robot, will need to be fabricated and assembled. For I2C switching of the magntic angle sensor boards, a circuit will need to be assembled (e.g. on a breadboard) from the schematic shown in the `hardware/electronic_circuits/LHR Circuit Diagrams.pdf` file. Additionally, a 5V-to-3.3V level shifter will need to be placed on the the I2C clock and data lines between the I2C switching circuit and the angle sensor boards, as the angle sensors require 3.3V power and logic while the Arduino operates on 5V power and logic.

Wiring and pin connections for the Arduino are shown in the `hardware/electronic_circuits/LHR Circuit Diagrams.pdf` file. Note that wires for the I2C signal lines must be kept as short as possible in order to mitigate radio frequency interference on those wires, which manifests as freezes in the Arduino software requiring a hard reset of the Arduino.

### Software Usage

Instructions for software setup and usage can be found in the README for [github.com/ethanjli/liquid-handling-robotics](https://github.com/ethanjli/liquid-handling-robotics#readme)
