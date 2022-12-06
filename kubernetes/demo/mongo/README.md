# Mongo Demo
## steps
- kubectl apply -f mongodb-secret.yaml
    - 註冊 secret 提供 deployment 使用
- kubectl apply -f mongodb.yaml
    - 註冊 deployment and service
    - 透過 mongodb-secret.yaml data 的 key mongousername, mongopassword 設定帳號密碼
    - secret data 的 value 存放 base64 編碼後的值 