# Dateimanagement
  
## Copy in oder aus einem Container
```docker cp SOURCE TARGET```
Hostverzeichnis kann Absolut oder Relativ angegeben werden  
Containerverzeichnus muss mit `Containername:` beginnen (z.B. `my-container:/application`)  
```
docker cp /projects/blog/index.html my-blog:/application/index.html
docker cp my-blog:/application/app.log /projects/blog/app.log
```
  
## Mounts
### bind
verknüpfung zwischen Host und Container  
Performanseintensiv wegen syncronisierung  
```
--mount type=bind,source={Hostpfad},destination={Containerpfad}
-v {absoluter Hostplfad}:{Containerpfad}
```
Hostpfad muss hier absolut sein, da sonnst andere bedeutung  
für Readonly am ende ein `:ro` anhängen  
  
### volume
eigenständiger Speicher innerhalb eines/mehrere Container
docker-optimiert  
```
--mount type=volume,source={Volumename},destination={Containerpfad}
-v {Volumename}:{Containerpfad}
```

### tmpfs
Daten werden in Arbeitsspeicher geschrieben  
nur unter Linux verfügbar/benutzbar

## Volumes
```
docker volume ls
docker volume create {Name}
docker volume inspect {Name}
docker volume rm {Name}
docker volume prune
```
Volumes befinden sich auf dem Hostsystem, sind aber nicht via docker manipulierbar  