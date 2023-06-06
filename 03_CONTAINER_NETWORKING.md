# Container Networking


## Commands
```
docker [container] start -d
docker run -d
```
startet den Container im detached-Mode (Hintergrund)  
  
```
docker [container] start --restart=always
docker run --restart=always
```
startet den Container mit bestimmten restart-Policy (Neustartbefehle)  
-- always = start Container immer wieder neu
-- unless-stopped = startet Container neu sofern nicht händisch gestoppt
-- on-failure[:max-retries] = startet Container neu, wenn ein Fehler aufgetretten ist (mit maximal x Versuchen)  
  
```
docker [container] start -p Hostport:Containerport
docker run -p Hostport:Containerport
```
leitet einen Port vom Host System in den Container weiter  