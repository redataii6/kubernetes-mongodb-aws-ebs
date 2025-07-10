# MongoDB & Mongo-Express on Kubernetes 
<img width="1919" height="1029" alt="Screenshot 2025-07-10 141132" src="https://github.com/user-attachments/assets/33f3e51c-60f9-4100-a0c1-e37d90e13f0e" />

Kubernetes deployment for MongoDB with persistent storage and Mongo-Express admin UI.


## Architecture

<img width="1497" height="641" alt="diagram-export-7-10-2025-2_57_15-PM" src="https://github.com/user-attachments/assets/a34ca12c-4965-4fca-8e9d-763db051acd8" />


## Features
- Persistent storage using AWS EBS
- Secure credential management with Kubernetes Secrets
- External access via LoadBalancer
- Auto-provisioned storage

## Deployment
```bash
kubectl apply -f deploy/

Access
Mongo-Express URL: http://<loadbalancer-ip>:8081
Default credentials: naeme-secret / password-secret


Components
Resource	Purpose
mongodb-pass (Secret)	Stores DB credentials
mongodb-sc (SC)	AWS EBS storage class
mongodb-pvc (PVC)	Persistent volume claim (5Gi)
mongodb-app (Deploy)	MongoDB deployment
mongodb-svc (Service)	MongoDB cluster IP service
mongo-cm (ConfigMap)	Stores DB connection URL
mongo-express (Deploy)	Web UI deployment
mongo-express-svc (Svc)	External access (NodePort 31000)

