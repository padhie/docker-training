# Troubleshooting

## docker cannot connect to the docker daemon at unix:///var/run/docker.sock. is the docker daemon running?  
- User ist nicht berechtigt docker zu verwenden  
- $ systemctl start docker  
- $ gpasswd -a $USER docker  
  
## Bind for 0.0.0.0:80 failed  
- Port ist bereits belegt  
- ggf. durch nginx oder apache  
  
## Container A verbindet nicht zu Container B  
- Laufen beide Container?  
- Sind beide Container im gleichen Netzwerk?  
- Passt die IP / Portfreigabe?  
  
## wie heißt mein Image
- mit `docker ps` kann man alle images einsehen  
- nach dem `docker build` steht der hash am Ende vom Output  
`writing image sha256 c3048814e....`  