# Netzwerk
  
```
docker network ls
docker network create {Netzwerkname}
docker network inspect {Netzwerkname} 
docker network rm {Netzwerkname}
```
es können nur Netzwerke vom Typ `bridge` angelegt werden
  
## Typen
### bridge
verbindet mehrere Container untereinander (kein zugriff von Host in das Netzwerk)  
immer im Subnetz `127.x.x.x`  

### host
wie bridge nur, dass Host mit in dem Netzwerk hängt  
  
### none / null
Netzwerk ist für den Container deaktiviert  

# Nachträglich anhängen/trennen
```docker network connect {Netzwerkname} {Containername}```
Container wird in das Netzwerk "eingehangen"  
  
```docker network disconnect {Netzwerkname} {Containername}```
Container wird aus dem Netzwerk "ausgehangen"