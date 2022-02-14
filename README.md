# GrafanaK8S

Deploy de Grafana K8S

Pour s'assurer qu'on ai toujours un pod fonctionel on va réaliser un déploiement

  -> grafana-deployment.yaml

On aura besoin de garder certaines data malgrès le fait que l'on relance le pod ou autres, pour ca notre deploy utilise un Volume peristent

  -> grafan-pvc.yaml 
  
Il faudra aussi créer un service pour expose notre deploy

  -> grafana-service.yaml
  
        kubectl create -f grafana-deployment.yaml -f grafana-service.yaml -f grafana-pvc.yaml 
