## Brief summary of guide

### In this guide, you will learn how to run Docker containers with Systemd and manage it with systemctl
# -----------------------------------------------------------------------------
### **Prerequisites**

This guide requires Linux, Git and Docker installed on your machine, we will run minio, but you can run also ( cassandra, rabbitmq, postgres ) pick from unit_files dir, list will be supplemented
          
### **Steps 1/2. Clone repository and run container**
# -----------------------------------------------------------------------------

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

### **Step 2/2. Check the status of service**
# -----------------------------------------------------------------------------

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
### Known issues and how-to solve them
# -----------------------------------------------------------------------------

1. If you already have such a service running on your computer, you may encounter conflicts, so first make sure there is no *.service that matches your new service.

### How to delete service and container completely
# -----------------------------------------------------------------------------

```
sudo systemctl stop minio.service
```
```
sudo rm -rf /etc/systemd/system/minio.service 
```
```
docker rm -f docker_mino
```
```
docker rm -f docker_minio 
```
make sure that container removed successfully

```
docker ps 
```
ouput should be: 
```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
and nothing else ( if you didn't run any containers by yourself )

### Conclusion
# -----------------------------------------------------------------------------

To conclude, since now, you know - how to run Docker containers with Systemd, and manage it with systemctl, you can start, stop, restart and look for status of service with "systemctl" command.