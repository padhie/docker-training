# Docker Kubernetes
* Container-Verwaltungstool   
* nicht nur für Docker möglich   
* deutlich mehr umfang als Docker-Swarm   
* stellt keine Anwendung zur verfügung! (nur die verwaltung)   

## Pod
* kleinste Einheit in Kubernetes   
* hier läuft die jeweilige Anwendung   


## Kubernetes Netzwerk/Cluster
* Cluster = 1-n Node (worker nodes)   
* Paxis: 1 Node = x Pods
* Controll Plane = Steuerungsebene (kann mit auf einem Node laufen um Server zu sparen)   
* Steuerungsebene
** kube-apiserver = Entrypoint (Frontend + API)
** etcd = Konfigurationsspeicher
** kube-scheduler = Verteilung auf die Pods
** kube-controller-manager = überwachung der Nodes/Pods
** cloud-controller-manager = kube-controller-manager als Cloud-Anbieter-Lösung   

## Unterschied Kubernetes vs. Docker Swarm
* Kubernetes ist deutlich komplexer und hat sich durchgesetzt
* wird oft von Cloud-Anbietern zur verfügung gestellt
* für lokal eher "Minikube" (resourcenschonender)
* Docker Swarm speziell auf Docker zugeschnitten und einfach zu verwenden
** funktioniert nur mit Docker Container
** eigenes Monitoring auf Docker ausgelegt
** nur Docker CLI
* Kubernetes für generelle Lösung und für ein großes Business geeigneter
** mehr kontrolle
** mehr konfiguration
** umfangreicheres Featureset

## Minikube
* virtualisiert ein Kubernetes-Cluster lokal
* nur für Entwicklung/Testen ausgelegt, kein Produktivbetrieb!

## kubectl
* CLI-Tool für Kubernetes-Cluster
* Kommunikation mit kube-apiserver
* Commands:
** kubectl version -> gibt version aus
** kubectl get [RESSOURCE] -> information zu einer bestimmten Ressource
*** kubectl get nodes -> infos über alle nodes
*** kubectl get pods -> infos über alle pods