# Mongo Demo
## steps
- . apply_kube.sh
  - apply all kube yaml in mongo
  
- mongodb-secret.yaml
    - 註冊 secret 提供 deployment 使用
  
- mongodb.yaml
    - 註冊 deployment and service
    - 透過 mongodb-secret.yaml data 的 key mongousername, mongopassword 設定帳號密碼
    - secret data 的 value 存放 base64 編碼後的值 

- mongo-configmap.yaml
  - 註冊 config map
  
- mongo-express.yaml
  - 註冊 mongo-express deployment, service
  - mongodb-secret.yaml 取得 mongodb username, password
  - mongo-configmap 取得 database_url
  - mongo-express-service 多數情境 service無需定義為external ip, 將type: LoadBalancer, nodePort: 30000 移除，port-forward 測試即可
  
- mongo-ingress.yaml
  - 註冊 ingress forward 到 mongo-express-service
  - 啟用 minikube 提供的 ingress entry point
    - minikube addons enable ingress
  - 定義 /etc/hosts >> 127.0.0.1 mongo.express 