# Container & Images

## DockerHub
- (DockerHub)[https://hub.docker.com/]  
- aufpassen auf Offizielle, Verifizierte und Community Images  
-- Offizielle -> geprüft und für sicher empfunden von DockerHub  
-- Verifiziert -> Benutzer ist geprüft und ist vertrauenswürdig - Image ist ungeprüft  
-- Community -> Benutzer und Image ist nicht geprüft  
  
## Images
Image[:Tag]  
- Tag = spezifische Version des Image
- Tag ist optional
- wenn kein Tag angegeben -> immer das aktuellste stable (kein Beta oder preview)  
  
## Commands
```docker [image] pull```  
lade ein Image herunter  
  
```docker image rm```  
Image lokal löschen  
  
```docker [container] create```  
erstelle ein Container anhand eines Image
  
```docker [container] start```  
start ein existierenden Container  
  
```docker [container] stop```  
stoppt einen laufenden Container
  
```docker run```  
pull + create + start  
erstellt *IMMER* ein neuen Container  
  
```
docker container ls [-a] [-s]
docker ps [-a] [-s]
```
listet alle aktiven Container auf (mit -a auch inaktive) (mit -s auch den speicher)  

```docker container inspect```  
listet Metadaten eines Container auf  

```docker rm```  
löscht einen Container  
  
```docker exec```  
ein Programm in dem Container ausführen (z.B. `bash`)  