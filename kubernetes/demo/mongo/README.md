# Mongo Demo
## steps
- kubectl apply -f mongodb-secret.yaml
    - 註冊 secret 提供 deployment 使用
- kubectl apply -f mongodb.yaml
    - 註冊 deployment and service
    - 透過 mongodb-secret.yaml data 的 key mongousername, mongopassword 設定帳號密碼
    - secret data 的 value 存放 base64 編碼後的值 

- kubectl apply -f mongo-configmap.yaml
  - 註冊 config map
  
- kubectl apply -f mongo-express.yaml
  - 註冊 mongo-express deployment and service
  - 透過 mongodb-secret.yaml data 的 key mongousername, mongopassword 設定帳號密碼
  - 透過 mongo-configmap 定義的 database_url 設定 database_url
  - mongo-express-service 大部分情境 service不需要定義為external, 可將 type: type: LoadBalancer, nodePort: 30000 移除，使用kubectl port-forward 測試即可