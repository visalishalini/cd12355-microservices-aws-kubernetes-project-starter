# Coworking Space Service Extension

# ECR Image Uploaded Via CodeBuild Pipeline
![image](https://github.com/user-attachments/assets/cf6001a3-f08e-40eb-a4d0-3906b7892496)

# CodeBuild History & Status
![image](https://github.com/user-attachments/assets/c41641e2-0d89-4343-993a-03c1e26a1e28)

# Build Details:
![image](https://github.com/user-attachments/assets/33f532e8-328d-4839-845c-f40bbf99a848)

# CodePipeline Trigger:
![image](https://github.com/user-attachments/assets/55863d95-3aaa-4dd1-85a4-ab193730a5cf)

![image](https://github.com/user-attachments/assets/e2ef516f-2299-4b40-abfb-a9e369c98700)

# $ kubectl get svc
NAME TYPE CLUSTER-IP EXTERNAL-IP
PORT(S) AGE
coworking LoadBalancer 10.100.152.144
ab3de8987e78447b39319de953930afa-1845413785.us-east-1.elb.amazonaws.com
5153:32495/TCP 25s
kubernetes ClusterIP 10.100.0.1 <none>
443/TCP 2d1h
postgresql-service ClusterIP 10.100.201.88 <none>
5432/TCP 47h

![image](https://github.com/user-attachments/assets/4229c2d6-fa9c-42b0-bb81-ed6a5fe57130)

# $ kubectl get deployment coworking
NAME READY UP-TO-DATE AVAILABLE AGE
coworking 1/1 1 1 75m

![image](https://github.com/user-attachments/assets/687700d6-2f73-4ef7-bc19-1bc6d5437815)

# $ kubectl describe deployment coworking
Name: coworking
Namespace: default
CreationTimestamp: Fri, 09 Aug 2024 17:39:08 +0100
Labels: name=coworking
Annotations: deployment.kubernetes.io/revision: 1
Selector: service=coworking
Replicas: 1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType: RollingUpdate
MinReadySeconds: 0
RollingUpdateStrategy: 25% max unavailable, 25% max surge
Pod Template:
Labels: service=coworking
Containers:
coworking:
Image: 387581210505.dkr.ecr.us-east-1.amazonaws.com/udacity3:test0908
Port: <none>
Host Port: <none>
Liveness: http-get http://:5153/health_check delay=5s timeout=2s period=10s
#success=1 #failure=3
Readiness: http-get http://:5153/readiness_check delay=5s timeout=5s
period=10s #success=1 #failure=3
Environment Variables from:
dbconfig ConfigMap Optional: false
Environment:
DB_PASSWORD: <set to the key 'DB_PASSWORD' in secret 'dbsecret'>
Optional: false
Mounts: <none>
Volumes: <none>
Node-Selectors: <none>
Tolerations: <none>
Conditions:
Type Status Reason
---- ------ ------
Available True MinimumReplicasAvailable
Progressing True NewReplicaSetAvailable
OldReplicaSets: <none>
NewReplicaSet: coworking-cb5fd4b4c (1/1 replicas created)
Events: <none>

![image](https://github.com/user-attachments/assets/b64ffc4d-bbc1-42d9-aca9-2d24c9878351)

# $ kubectl get pods -A
NAMESPACE NAME READY STATUS
RESTARTS AGE
amazon-cloudwatch
amazon-cloudwatch-observability-controller-manager-66b877bp4rsp 1/1 Running
0 40m
amazon-cloudwatch cloudwatch-agent-qgpb7 1/1
Running 0 39m
amazon-cloudwatch fluent-bit-d4cmw 1/1 Running
0 40m
default coworking-cb5fd4b4c-7flm9 1/1 Running
0 75m
default postgresql-77d75d45d5-snvj7 1/1 Running
0 2d
kube-system aws-node-42bm5 2/2 Running
0 2d2h
kube-system coredns-586b798467-2gw4p 1/1
Running 0 2d2h
kube-system coredns-586b798467-75jz9 1/1
Running 0 2d2h
kube-system kube-proxy-zsqkt 1/1 Running 0
2d2h

![image](https://github.com/user-attachments/assets/e18b6d50-92bd-4a89-8aff-b27c5706b9c6)

# $ kubectl describe service postgresql-service
Name: postgresql-service
Namespace: default
Labels: <none>
Annotations: <none>
Selector: app=postgresql
Type: ClusterIP
IP Family Policy: SingleStack
IP Families: IPv4
IP: 10.100.201.88
IPs: 10.100.201.88
Port: <unset> 5432/TCP
TargetPort: 5432/TCP
Endpoints: 192.168.20.244:5432
Session Affinity: None
Events: <none>

![image](https://github.com/user-attachments/assets/0f59c0ad-fbb5-4db3-b7c5-621f20c93da9)

# CloudWatch Log Groups:
![image](https://github.com/user-attachments/assets/29a13f97-6b97-43ef-a161-49aff374ef7b)

# CloudWatch LogStream for Application
![image](https://github.com/user-attachments/assets/8545915f-8116-4d5b-a8da-7b9c61761ac3)

# External IP of LoadBalancer:
ab3de8987e78447b39319de953930afa-1845413785.us-east-1.elb.amazonaws.com

# Testing of daily_usage & user_visits api via curl:
![image](https://github.com/user-attachments/assets/873b9b2d-d441-420a-a84e-f7ebe3dd8dc9)


