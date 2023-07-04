# Dockerfiles 2

## Metadaten
erst nach dem `FROM` erlaubt

```
LABEL [KEY]=[VALUE]
```

## .dockerignore
Dateien/Verzeichnise die beim Build ignoriert werden (ähnliche wir .gitignore)  
funktioniert nur von host zu Dockerbuild   


## CPU-Architektur (ARM vs. x86)
x86 (linux/amd64) bisher eher auf PC und Laptop   
ARM (linux/arm64) bisher eher auf Smartphone und Tablet   
ARM auch bei MacBook und tendenz auch zu normalen PC/Laptop   

Mit `--platform=linux/amd64` kann man x86 container auf ARM-CPU ausführen lassen   
-> sehr starke Performance-Einbuße   

## Alpine
musl statt glib (GNU C Lib)   
apk statt apt (Paketmanger)   
sehr klein - bringt nur was, wenn das als Mehrfachtes Basisimage verwendet werden

## musl vs. glibc
unterschiedliche Runtime-Lib    
glibc: Standard unter Linux   
musl: kleiner und "moderner" & enthält nicht unbedingt alle "optimierungen" die glibc enthält   
Unterschiedliches verhalten (z.B. Speicheradressen zuweisung oder "%Z" der Python-Funktion strftime nicht implementiert)   
bei musl müssen ggf. applicationen selbst compeliert werden (weil nicht als Binär-Datei vorhande)    

## Multi-Stage Build
Primär ausgelegt um kleine Images zu haben trotzdem vorher großem Aufwand (Programme compelieren aber die Compelier-Libs nicht weiter benötigt).   
Eine ausführbarers Programm erst compelieren und dann in einem kleinen Image nur Programm haben.   

```
FROM erstes Image
compile Application

FROM zweites Image
COPY --from=0 [Datei vom ersten Image] [Ort im zweiten Image]
```
Stages werden durchnummeriert (oder können per `AS` benannt werden)   
auch mehrere Stages möglich   
