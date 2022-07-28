# Setup Keda in Kubernetes cluster

* Installing Keda in kuberentes cluster is fairly simple process
* We are going to use helm to install Keda

## Prerequsites

* Have kubernetes cluster ready
* Have helm installed in your kuberenets cluster

## Kubernetes installation tools

| Local      | AWS | GCP |
| ---------- | --- | --- |
| Minikube   | EKS | GKS |
| Kubeadmin  |     |     |
| Virtualbox |     |     |
| Vagrant    |     |     |

## Helm installation
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## Keda installation
```
helm repo add kedacore https://kedacore.github.io/charts
helm repo update
kubectl create namespace keda
helm install keda kedacore/keda --namespace keda
```
