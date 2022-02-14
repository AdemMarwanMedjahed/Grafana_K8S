# Grafana K8S

Nous allons assurer un deploiement K8S de Grafana pour étudier les datas de nos 

---
Pour s'assurer qu'on ait toujours un pod fonctionnel on va réaliser un déploiement

    grafana-deployment.yaml

On aura besoin de garder certaines data malgré le fait que l'on relance le pod ou autres, pour ça notre deploy utilise un Volume persistant

    grafana-pvc.yaml 
  
Il faudra aussi créer un service pour exposer notre deploy

    grafana-service.yaml
  
 Créeons nos objets K8S :
  
        Kubectl create -f grafana-deployment.yaml -f grafana-service.yaml -f grafana-pvc.yaml 

Cas d'entreprise ou particulier, on pourras en plus d'exposer a l'aide d'un service passer par un Ingress pour parametrer un host
Il faudra penser a modifier notre fichier /etc/hosts

        kubectl apply -f grafana-ingress.yaml

Petite astuce pour voir et installer les plugins sur notre pod : 
        
        Plugins installés:
        kubectl exec -it grafana-nompod grafana-cli plugins ls
        ---
        Plugins disponible : 
        kubectl exec -it grafana-nompod grafana-cli plugins list-remote
        ---
        Installation plugin : 
        kubectl exec -it grafana-nompod grafana-cli plugins install grafana-kubernetes-app
        
        
Grafana CLI doc : https://grafana.com/docs/grafana/latest/administration/cli/
