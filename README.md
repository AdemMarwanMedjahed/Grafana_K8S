# Grafana K8S

Deploy de Grafana K8S

Pour s'assurer qu'on ait toujours un pod fonctionnel on va réaliser un déploiement

grafana-deployment.yaml

On aura besoin de garder certaines data malgré le fait que l'on relance le pod ou autres, pour ça notre deploy utilise un Volume persistant

  -> grafana-pvc.yaml 
  
Il faudra aussi créer un service pour exposer notre deploy

  -> grafana-service.yaml
  
 Créeons nos objets K8S :
  
        Kubectl create -f grafana-deployment.yaml -f grafana-service.yaml -f grafana-pvc.yaml 

Cas d'entreprise ou particulier, on pourras en plus d'exposer a l'aide d'un service passer par un Ingress pour parametrer un host
Il faudra penser a modifier notre fichier /etc/hosts

        kubectl apply -f grafana-ingress.yaml

