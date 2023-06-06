# Dockerfiles & Multi-Stage build

## Dockerfile
Vereinfachung eines wiederholbares aufsetzen (keine 20 cli commands jedes mal neu)  
  
Datei: `Dockerfile` (ohne Endung)  
Syntax: `[ANWENDUNG] [Parameter]`  
Konvention: `[ANWENDUNG]` immer groß schreiben  
Kommentar: `#` am anfang der Zeile  
  
### Kommandos
Basiscommand
```
docker build {Pfad}
```
  
baue ein image mit einem Dockerfile im gleichen Verzeichnis
```
docker build .
```
  
baue ein image mit einem Dockerfile im anderen Verzeichnis
```
docker build {Pfad zum Verzeichnis}
```
  
baue ein image mit einem Dockerfile mit anderen namen
```
docker build -f {Pfad & Datei} .
```
  
### Syntax
`FROM {Image}[:tag]` - Basisimage ggf. mit tag  
`RUN {Anweisung}` - führt ein CLI-Command aus für die Basisconfiguration (OHNE Interaction)  
`COPY {Quelle} {Ziel}`  - kopiert Daten von Lokal in das Image  
`ADD {Quelle} {Ziel}` - gleiche wie `COPY`, kann auch von URL laden oder entpacke
`CMD ["Programm / Datei", "Parameter 1", ...]` - fürt eine Anwendung mit bash aus  
`CMD "Programm / Datei", "Parameter 1", ...` - führt eine Anwendung mit shell aus  
`ENTRYPOINT ["Programm / Datei", "Parameter 1", ...]` - gleiche wie `CMD` nur nicht überschreibbar  
`WORKDIR {PFAD}` - setzt Arbeitsverzeichnis (anstelle von cd {PFAD})  
`ARG foo=bar` - setzt eine Variable (nur für den Buildprozess)  
`ENV FOO=bar` - setzt eine Variable (im Build- und ausführprozess)  
`VOLUME {Volumename}` - erstellt ein Image im Buildprozess  
`EXPOSE {Port}[/Protocol]` - hört auf ein Port (default Protocol: TCP)  
`STOPSIGNAL {Signal}`- senden beim Container stoppen ein Signal an die laufende Anwendung (z.B. nginx)  
  
Jeder `RUN` Befehl = 1 Layer / Schicht  
Mehr `RUN` Befehle = mehr Layer = Image wird größer = bauen dauer länger  
`CMD` kann über die CLI eingabe überschrieben werden  
`ENTRYPOINT` alle übergebenen Parameter werden angehangen (nicht überschrieben wir bei `CMD`)  
`ENTRYPOINT` und `CMD` kombinierbar -> erst kommt `ENTRYPOINT` dann `CMD` (für Service-Container) 