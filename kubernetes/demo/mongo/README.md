# Mongo Demo
## steps
- 依序 apply 以下檔案(有相依性順序重要)
  - 依序 apply
    - kubectl apply 1-mongodb-namespace.yaml
    - kubectl apply 2-mongo-configmap.yaml
    - kubectl apply 3-mongodb-secret.yaml
    - kubectl apply 4-mongodb.yaml
    - kubectl apply 5-mongo-express.yaml
    - kubectl apply 6-mongo-ingress.yaml
  - 或直接執行 apply_kube.sh 兩種方式擇一
  
- 1-mongodb-namespace.yaml
    - 配置 mongodb namespace

- 2-mongo-configmap.yaml
  - 註冊 config map, 設定 mongodb database_url
  
- 3-mongodb-secret.yaml
    - 配置 mongodb admin password
  
- 4-mongodb.yaml
    - 註冊 deployment and service
    - 透過 mongodb-secret.yaml data 的 key mongousername, mongopassword 設定帳號密碼
    - secret data 的 value 存放 base64 編碼後的值
  
- 5-mongo-express.yaml
  - 註冊 mongo-express deployment, service
  - mongodb-secret.yaml 取得 mongodb username, password
  - mongo-configmap 取得 database_url
  - mongo-express-service 多數情境 service無需external ip, 將type: LoadBalancer, nodePort: 30000 移除，port-forward 測試即可
  
- 6-mongo-ingress.yaml
  - 註冊 ingress forward 到 mongo-express-service
  - 定義 /etc/hosts >> 127.0.0.1 mongo.express
  - 啟用 minikube 提供的 ingress entry point
    - minikube addons enable ingress
    - minikube tunnel
  
- 訪問 mongo.express
- 查看 namespace
  - kubectl get all -n mongodb
  - kubectl describe namespace mongodb
  - kubectl get pod -n mongodb -o yaml

