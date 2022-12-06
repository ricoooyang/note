# kubectl CLI
- kubectl create -f xxxx.yaml
- kubectl get pod
- kubectl get pod -o wide
- kubectl get deploy
- kubectl get deploy {deployment name} -o yaml (get deployment status from etcd)
- kubectl get services
- kubectl get ingress
- kubectl describe pods
- kubectl describe po -l name=myLabel
- kubectl describe service {service name}
- kubectl delete -n default pod {pod name}
- kubectl delete all --all --all-namespaces
- kubectl delete ingress {ingress name}
- kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission
- kubectl expose deployment nighter-customer-site-deployment --type=LoadBalancer --port=80
- kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.0/deploy/static/provider/cloud/deploy.yaml

# minikube CLI
- minikube start
- minikube stop
- minikube ip
- minikube ssh
- minikube addons enable ingress
- minikube dashboard
