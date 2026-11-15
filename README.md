[Exercise 0: Pre-KiCad SPICE Verification (LTspice)]

* Circuit Modeling (L1): Simulated a discrete CMOS inverter utilizing Q1

  (2N7000 NMOS) and Q2 (BS250 PMOS) driving an output LED and current-limiting

  resistor (R1) at VDD = 5 V.

* DC Transfer Analysis (L2): Swept VIN from 0 V to 5 V (0.01 V steps) to

  extract the switching threshold Vm (VOUT = VDD/2) and evaluated dead-zone

  behavior at VDD = 5 V vs. VDD = 9 V.

* Transient & Load Metrics (L3): Measured static LED current (I_LED) at

  VIN = 0 V against theoretical (VDD - V_F)/R1, and extracted 10-90% rise (t_r)

  and fall (t_f) times using a 1 kHz pulse input.

* Python Post-Processing & Scaling Comparison (L4-L5): Reproduced the Voltage

  Transfer Characteristic (VTC) at 300 DPI via pandas and compared normalized

  VTC curves (VOUT/VDD vs. VIN/VDD) against a 65 nm integrated CMOS inverter.



[Exercise 1: Schematic Capture & ERC (KiCad Schematic Editor)]

* Constructed the full circuit schematic (<roll>_INV.kicad_sch) with Q2 oriented

  so its source connects to the +5V rail.

* Configured power distribution nets (+5V, GND) with PWR_FLAG symbols and

  routed wiper (POT_W) and input (VIN) nets to header J2.

* Verified schematic integrity with 0 ERC errors and 0 warnings.



[Exercise 2: Footprint Assignment & Pinout Verification]

* Cross-referenced physical package pinouts (Source, Gate, Drain) from the

  manufacturer datasheets for the 2N7000 and BS250 against KiCad symbol pin

  numbering.

* Assigned all eight component footprints and synchronized schematic changes

  to the PCB editor (F8) with 0 errors and 0 warnings.



[Exercise 3: PCB Layout, Routing & DRC (KiCad PCB Editor)]

* Board Geometry: Defined a 50 x 40 mm board outline on Edge.Cuts with four M3

  mounting holes inset 4 mm from the corners.

* Routing & Copper Pour: Assigned +5V and GND to a dedicated Power net class,

  routed all signal/power tracks, and poured a bottom-layer (B.Cu) ground

  plane with thermal reliefs.

* Silkscreen & Verification: Added board identification (CMOS INVERTER and

  roll number) on F.Silkscreen (>= 1 mm clearance from board edges) and achieved

  0 DRC violations, 0 unconnected items, and 0 schematic parity errors.



[Exercise 4: Manufacturing Outputs (GerbView & BOM)]

* Generated Gerber plot files and drill files into gerbers/.

* Visually inspected alignment, drill hits, and silkscreen layers in GerbView.

* Exported the Bill of Materials (CSV) and packaged the fabrication archive

  (<roll>_INV_gerbers.zip).



[Exercise 5: Design Explorations (Optional)]

* Explored single-variable hardware modifications through simulation, layout,

  and Gerber generation:

  1. Cascading a second inverter stage to form a non-inverting buffer.

  2. Reconfiguring the LED load to active-low operation.

  3. Increasing minimum trace/copper clearance to 0.4 mm for low-cost

     fabrication rules.

  4. Replacing the onboard trimpot with a 2-pin external input header and

     minimizing board area.
