# Docker Compose

sehr aufwendig mehrere Dockerfiles zu verknüpfen.   
compose.yaml (docker-compose.yaml ist nur für Abwertskompatibilität verfürbar)   
erstellt automatisch ein neues Netzwerk (auch wenn man nichts genauer spezifiziert)    

## Exkurs: YAML
**Y**AML **a**in't **M**arkup **L**anguage   
ähnlich wie XML/JSON aber für Menschen lesbarer   
**.yml** oder **.yaml**   
Einrückungs-Syntax   
[json2yaml](https://www.json2yaml.com/) converter   
```yaml
stringA: normal string without quotes
stringB: "string with quotes cause we have a \nlinebreak"

arrayA:
	- Value 1
	- Value 2
	- Value 3
arrayB:
	- key: one
	  value: 1
	- key: two
	  value: 2

variable: &student Max Musterman
reference: *student
```

## compose.yaml
* `version` -> [optional|default 3] version von YAML (3 ist aktuell, 2 ist veraltet)   
* `services` -> [required] ein Service entspricht einen Container   
  * `image` -> Basisimage   
  * `build` -> Dockerfile    
  * `volumes` -> persistenter Speicher - entspricht `--volumes`   
  * `ports` -> Portdefinition (Host:Container) - entspricht `--port Host:Container`   
  * `environment` -> ENV-Variable - entspricht `-e`   
  * `command` -> command nach dem start ausgeführt wird   
  * `restart` -> angabe ob/wann der Container neu gestartet werden kann (no, always, on-fail, unless-stopped) - entspricht `--restart=`   
  * `expose` -> Portfreischaltung   
  * `depends_on` -> aktueller Service benötigt einen anderen Service (prüft nicht ob andere Service korrekt laufen)   
  * `container_name` -> Container-name   
  * `scale` -> [deprecated|use deploy.replicas] angabe wie oft ein Container gestartet werden soll   
  * `deploy` -> verschiedene Einstellungen für den fertigen/laufenden Service (z.B. Service mehrfach laufen lassen)   
  * `links` -> Serive mit einem anderen Service verlinken   
  * `secrets` -> Sensible/Vertrauliche Daten
* `volumes` -> Volumes können genauer definiert werden (z.B. name oder driver)

## Command
compose.yaml muss im aktuellen Verzeichnis liegen   

`docker compose up` -> startet alle Services   
`docker compose down` -> fährt die Services herunter   
`docker compose stop` -> stoppt die Services    
`docker compose start` -> startet die Services   
`docker compose pause` -> Service werden pausiert   
`docker compose unpause` -> Service werden weiter geführt (nach `docker compose pause`)   
`docker compose exec [Service] [Programm]` -> führt das angegeben Programm im angegebenen Service aus -> equivalent zu `docker exec -it [Container] [Programm]`   

`docker compose` cached die `compose.yaml` Datei - muss mit `--build` angefordert werden     

## Environments von extern
in Container: `${ENVORINMENT_NAME}`   
auf der CLI übergeben: `ENVORINMENT_NAME=value docker compose up`   
alternativ die OS varianten verwenden (z.B. `export ENVORINMENT_NAME=value` -> `docker compose up`)   
   
docker unterstützt auch `.env`-Dateien   
