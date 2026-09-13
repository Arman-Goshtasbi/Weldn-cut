# Weld n'Cut

**An open-source, automated platform for fabricating textile-based inflatable soft actuators**, combining ultrasonic welding with precision oscillating-knife cutting.

[![Paper](https://img.shields.io/badge/paper-arXiv%3A2502.06361-b31b1b.svg)](https://arxiv.org/pdf/2502.06361)
[![Video](https://img.shields.io/badge/video-YouTube-red.svg)](https://www.youtube.com/watch?v=cfQpgHbBx4o)

Developed by SDU Soft Robotics, University of Southern Denmark (SDU).

## Overview

Textile-based inflatable soft actuators are usually made by heat-pressing fabric layers together with masking layers to define air chambers — a slow, manual, error-prone process. **Weld n'Cut** automates this with a single CNC gantry carrying:

- An **ultrasonic spot welder**, modified to be programmable, for fusing heat-sealable textiles with no masking, glue, or stitching.
- An **oscillating tangential knife**, for precisely cutting complex boundaries and kirigami patterns.

Weld and cut profiles are designed in Rhino/Grasshopper, converted to G-code, and run on the machine to produce airtight actuators — from simple pouches to bending, twisting, and kirigami-based designs.

## Repository contents

```
Weldn-cut/
├── Grasshopper/              # Parametric design files (.gh) for weld/cut G-code generation
├── Electronic Schematics/    # Circuit for the programmable ultrasonic welder
└── CAD files/                # SolidWorks parts for welder/cutter mounts and bed
```

## Requirements

- Rhinoceros 7 + Grasshopper
- SolidWorks (for the `.SLDPRT` files)
- UCCNC (or equivalent CNC controller)
- CNC gantry with an ultrasonic welder + oscillating knife (e.g., Stepcraft OTK-3)

## Citation

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
- 🎥 Video: [youtu.be/cfQpgHbBx4o](https://www.youtube.com/watch?v=cfQpgHbBx4o)
