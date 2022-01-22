# print-stuffz
## auto pid tune
`m303 sN` ... where N is target temp (usually 205 for pla)

`m301 pX iY dZ` ... where XYZ is the numbers from the m303 autotune

`m500` ...  autosave


## ender 3 pro start gcode profile
```
M140 S{material_bed_temperature} ; start preheating the bed WITHOUT wait to what is set in Cura
M104 S{material_print_temperature} ﻿T0 ; start preheating hotend WITHOUT wait to what is set in Cura
G28 ; Home all axes
;M420 S1 ; comment abl
G29 ; uncomment abl
M500 ; uncomment abl
M190 S{material_bed_temperature} ; start heating the bed to what is set in Cura and WAIT
M109 S{material_print_temperature} ﻿T0 ; start heating hotend to what is set in Cura and WAIT


; Ender 3 Custom Start G-code
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish
```
hole expansion: +0.1
