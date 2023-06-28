k8

#  kubectl delete deployment --all   --to delete all deployment
#  kubectl port-farword svc/<service name> <running port no>   --to expose a service ip service in minikube
# minikube ip    ---to get ip of minikube
# k apply -f <file name>
# 1. configmap  2.secrets  3.service  4.mongo-deployment   5.web-app.yml
# k describe pod -o wide
# k logs <resource_name>
# k exec -it <pod_name> -- /bin/bash    ---to enter inside the pod in single container
# k exec -it <pod_name> -c <cont._id> 

# k get pod
# k apply 
# kubectl delete deployment --all
# kubectl delete secret --all
# k delete configmap --all
# k delete pv --all

# k get all
# k 

# kubectl get svc -n lumina --lists all svs in lumina ns
# kubectl -n lumina port-forward service/webapp-service 30101:8081   ---expose the web app nodeport service on the port 30101 to access externally
# on url :     localhost:30101

# minikube service webapp-service -n lumina   ---

# kubectl get all -n lumina   ---lists all the services
# 
# kubectl -n lumina port-forward service/prometheus-kube-prometheus-prometheus 30102:9090    ---port forword the prometheus 
# 

# helm repo add grafana https://grafana.github.io/helm-charts      
# helm repo update

# helm install grafana grafana/grafana   ---to install grafana on cluster
# kubectl -n lumina port-forward service/grafana 30103:80
# kubectl get secret --namespace lumina grafana -o yaml  --to get secrets from grafana svc
# 

# k run custom-nginx --name=nginx --port=8080
# k create deployment redis-depoy --image=redis --replicas

# k get cm -n <ns>  to see all configmaps

#* HPA * 
# kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10    --to create hpa
# kubectl get hpa

# # Run this in a separate terminal
# # so that the load generation continues and you can carry on with the rest of the steps
# kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
# # type Ctrl+C to end the watch when you're ready
# kubectl get hpa php-apache --watch


# k get pod -o wide
















ps aux | grep vim       to show all processs
sudo kill <PID>         to kill the process


kubectl get nodes --show-labels
kubectl label nodes minikube minikube=master    to add labels 
                     node       label 
kubectl label nodes minikube minikube-    to remove label 

minikube profile list   to get all profiles in minikube 
minikube start --nodes 2 -p newprofilename           to start minikube with multinode
minikube delete -p multinode-demo     to delete minikube profiles
minikube start -p multinode-demo
echo "you have been hacked" >> /dev/pts/6                       to send msg to another terminal 


HELM ......................................................................................................................................................
helm init: Initializes Helm on your cluster, installing Tiller (the server-side component of Helm) and setting up the necessary resources.

helm repo add: Adds a Helm repository to your local Helm configuration. Helm repositories contain packaged charts that you can install on your cluster.

helm search: Searches for available charts in the configured Helm repositories based on the specified keyword. It helps you find charts for the applications you want to deploy.

helm install: Installs a chart onto your Kubernetes cluster. You need to specify the name of the release, the chart name, and optionally provide values or a values file to customize the chart's configuration.

helm upgrade: Upgrades an existing release to a new version of the chart. You can use this command to update your deployed applications with new features or bug fixes.

helm uninstall: Uninstalls a release, removing all associated resources from your Kubernetes cluster.

helm list: Lists all the releases currently deployed on your cluster.
helm repo list 
helm status: Retrieves the status of a release, showing information about the deployed resources, version, and other details.

helm get: Retrieves additional information about a release, such as the deployed configuration, values, or specific resources.

helm package: Packages a directory or a chart into a compressed chart archive file (.tgz), which can be distributed and installed on a cluster.

helm repo update: Updates the local cache of Helm repositories, ensuring you have the latest versions of charts available.

helm rollback: Rolls back a release to a previous version, undoing a failed or unwanted upgrade.

helm list
helm delete my-release

helm install my-release oci://registry-1.docker.io/bitnamicharts/postgresql-ha --set \
 nodeSelector."minikube=master"=linux     add chart to specific node using labels
