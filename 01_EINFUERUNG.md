# Einführung

## VM-Architektur

```
Unsere Anwendung
   ^
Anwendungssoftware der VM     ----\
   ^                               --- OS (z.B. Ubuntu)
Kernel der VM                 ----/
   ^
Virtualle Maschine
   ^
--------------------------
   ^
Virtualisierungssoftware
   ^
Anwendungssoftware             ----\
   ^                                --- OS (z.B. Windows)
Kernel                         ----/
   ^
Pysikalische Hardware
```
  
  
## Docker-Architektur

```
Unsere Anwendung
   ^
Anwendungssoftware der VM
   ^
--------------------------
   ^
Kernel
   ^
Pysikalische Hardware
```