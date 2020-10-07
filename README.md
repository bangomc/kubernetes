Init Kluster

1. Initializes cluster master node:
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16

2. Initialize cluster networking:
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml

Deploy Kubernetes bootcamp
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1

Expose
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080

Scale
kubectl scale deployments/kubernetes-bootcamp --replicas=4

Update
kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2