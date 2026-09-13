# Weld n'Cut

**An open-source, automated platform for fabricating textile-based inflatable soft actuators, combining ultrasonic welding with precision oscillating-knife cutting.**

[![Paper](https://img.shields.io/badge/paper-arXiv%3A2502.06361-b31b1b.svg)](https://arxiv.org/pdf/2502.06361)
[![Video](https://img.shields.io/badge/video-YouTube-red.svg)](https://www.youtube.com/watch?v=cfQpgHbBx4o)

Developed by SDU Soft Robotics, Biorobotics Section, The Maersk Mc-Kinney Moller Institute, University of Southern Denmark (SDU).

---

## Overview

Lightweight, durable, textile-based inflatable soft actuators are widely used in soft robotics — especially in wearable robots for rehabilitation and for enhancing human performance in demanding jobs. Traditionally, fabricating these actuators requires fusing heat-sealable fabrics with a heat press and using non-stick masking layers to define internal air chambers. Removing those masking layers afterward is fiddly, labor-intensive, and error-prone.

**Weld n'Cut** addresses this by combining two tools on a single CNC gantry:

- An **ultrasonic plastic spot welder**, converted from a manual tool into a programmable one, for fusing heat-sealable textile layers together without masking layers, adhesives, or stitching.
- An **oscillating tangential knife**, for precisely cutting complex boundaries and kirigami-style cut patterns.

By welding and cutting in a single automated workflow, the platform removes the manual masking/unmasking step entirely, improving accuracy, repeatability, and scalability while enabling arbitrarily complex actuator geometries — from simple air pouches to pneumatic network (PneuNet) actuators and inflatable kirigami structures.

This repository contains the design files that accompany the paper *"Weld n'Cut: Automated fabrication of inflatable fabric actuators"* (arXiv:[2502.06361](https://arxiv.org/pdf/2502.06361)).

## How it works

1. **Design** — Weld and cut profiles are parametrically designed in Rhinoceros 7 / Grasshopper.
2. **G-code generation** — The Grasshopper definitions convert those profiles into G-code for the CNC machine.
3. **Layup** — A PTFE release sheet is placed on the machine bed, the textile layers are positioned on top (thermoplastic-coated sides facing each other), and another PTFE sheet is placed on top to protect the material during welding.
4. **Welding** — The ultrasonic welder is lowered via a motorized linear stage and executes the programmed weld pattern, fusing the layers and defining the internal air chambers.
5. **Cutting** — The welder is raised, the oscillating knife is activated, and it cuts the final outline and any internal kirigami features along the same coordinate system.
6. **Result** — An airtight, weld-bonded inflatable actuator, ready for connector attachment and pressurization.

The machine itself is built on a Cartesian CNC gantry (CNC-STEP High-Z S-720) with a 500 W ultrasonic spot welder (Baoshishan) and an oscillating tangential knife (Stepcraft OTK-3), coordinated over seven control channels using the open-source UCCNC (CNCDrive) machine-control software.

## Repository contents

```
Weldn-cut/
├── Grasshopper/                 # Rhino/Grasshopper (.gh) parametric design files
│   ├── SVG-DXF-DWG_2_GCode.gh       # Converts imported vector drawings (SVG/DXF/DWG) into weld & cut G-code
│   ├── Material_exploration.gh      # Test patterns used for material/weld-speed characterization
│   ├── Bending_actuator.gh          # Unidirectional / antagonistic bending PneuNet actuator
│   ├── Contraction_kirigami.gh      # Kirigami actuator with staggered linear cut patterns
│   ├── contraction_nocut.gh         # Linear contraction (PneuNet) actuator, weld-only
│   └── twisting_30deg.gh            # Twisting actuator with inclined weld lines
├── Electronic Schematics/
│   └── Electronic_schematic.pdf     # Circuit for converting the manual ultrasonic welder into a programmable, timed spot welder
└── CAD files/
    ├── Ultrasonic holder_.SLDPRT    # SolidWorks part: ultrasonic welder mount
    ├── Mountin_plate_cutter_welder.SLDPRT  # SolidWorks part: mounting plate for the cutter/welder assembly
    └── back_sheet.SLDPRT            # SolidWorks part: machine bed backing sheet
```

## Requirements

- **Rhinoceros 7** with **Grasshopper** (to open and edit the `.gh` parametric design files)
- **SolidWorks** (to open the `.SLDPRT` CAD files for the welder/cutter holders and machine bed)
- **UCCNC** (CNCDrive) or equivalent CNC controller software capable of running the generated G-code
- A CNC gantry system with:
  - An ultrasonic plastic spot welder, modified for programmable timed operation (see `Electronic Schematics/`)
  - An oscillating tangential knife (e.g., Stepcraft OTK-3) mounted on the z-axis
  - A motorized linear stage for independently positioning the welder

## Materials

The platform is designed for heat-sealable, thermoplastic-coated textiles (thermoplastic polymer such as PP, PE, nylon, or TPU on at least one face). Materials validated in the paper include TPU-coated nylon (light/medium/heavy weight), TPU-coated ripstop, PU-coated polyester, PU-coated nylon, and conductive fabric (Velostat). TPU-coated nylon was found to give the best balance of airtight bonding and flexibility, and was used for most of the demonstrated actuators. Recommended welding speeds range from roughly 100 mm/min (heavyweight textiles) to 250 mm/min (Velostat) — see the paper for the full breakdown by material and weight.

## Demonstrated actuators

The Grasshopper files in this repo can be used to reproduce the actuator classes demonstrated in the paper:

- **Linear (contraction) actuators** — fabric PneuNets that contract axially when inflated
- **Bending actuators** — unidirectional and antagonistic (bidirectional) bending, made by fusing textile layers of different stiffness
- **Twisting actuators** — created using inclined weld-line patterns
- **Kirigami actuators** — staggered linear cut patterns enabling large, tunable axial contraction and load-carrying capability

## Citation

If you use this platform or design files in your work, please cite:

```bibtex
@article{goshtasbi2025weldncut,
  title   = {Weld n'Cut: Automated fabrication of inflatable fabric actuators},
  author  = {Goshtasbi, Arman and Seyido{\u{g}}lu, Burcu and Murali Babu, Saravana Prashanth and Parvaresh, Aida and Do, Cao Danh and Rafsanjani, Ahmad},
  journal = {arXiv preprint arXiv:2502.06361},
  year    = {2025}
}
```

## Links

- 📄 Paper: [arXiv:2502.06361](https://arxiv.org/pdf/2502.06361)
- 🎥 Supporting video: [youtu.be/cfQpgHbBx4o](https://www.youtube.com/watch?v=cfQpgHbBx4o)
- 🏫 SDU Soft Robotics, Biorobotics Section, University of Southern Denmark

## Acknowledgements

This work was supported by the Independent Research Fund Denmark through the Sapere Aude grant 1051-00075B and the Villum Young Investigator grant 37499.

## Authors

Arman Goshtasbi†, Burcu Seyidoğlu†, Saravana Prashanth Murali Babu, Aida Parvaresh, Cao Danh Do, Ahmad Rafsanjani*
SDU Soft Robotics, Biorobotics Section, The Maersk Mc-Kinney Moller Institute, University of Southern Denmark (SDU), 5230 Odense M, Denmark

†These authors contributed equally · *Corresponding author
