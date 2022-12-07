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
  - 註冊 mongo-express deployment, service
  - mongodb-secret.yaml 取得 mongodb username, password
  - mongo-configmap 取得 database_url
  - mongo-express-service 多數情境 service無需定義為external ip, 將type: LoadBalancer, nodePort: 30000 移除，port-forward 測試即可