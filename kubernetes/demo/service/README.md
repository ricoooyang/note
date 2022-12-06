# Service Demo
## steps
- kubectl apply -f nginx-deployment.yaml
    - 建立 deployment
    
- kubectl apply -f nginx-service.yaml
    - 建立 service 為 nginx-deployment pods 的入口
    
- kubectl get pod -o wide
    - 查看 pods 的 ip

- kubectl describe service nginx-service
    - 查看 endpoints 為 pods 的 ip