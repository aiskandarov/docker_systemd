## Brief summary of guide

In this guide, you will learn how to run Docker containers on Systemd and manage it with Systemctl

### **Prerequisites**

This guide requires Linux and Docker installed on your machine

### **Steps 1/N. Step Clone repository and run continer**

```
git clone https://github.com/aiskandarov/docker_systemd.git && cd docker_systemd
```
```
sudo cp unit_files/minio.service /etc/systemd/system/
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl start minio.service
```

### **Step 2/N. Check the status of service**
```
sudo systemctl status minio.service
```
output should be:
```
● minio.service - MinIO object storage
Loaded: loaded (/etc/systemd/system/minio.service; enabled; vendor preset: enabled)
Active: active (running) since Tue 2023-11-28 10:11:19 UTC; 2 days ago
Main PID: 18983 (docker)
```
also check with:

```
docker ps
```
output should be:
```
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS         PORTS                                                           NAMES
119e441e8716   minio/minio:latest   "/usr/bin/docker-ent…"   10 seconds ago   Up 9 seconds   0.0.0.0:9000-9001->9000-9001/tcp, :::9000-9001->9000-9001/tcp   docker_minio
```
### Conclusion

To conclude,

### Known issues and how-to solve them

1.
