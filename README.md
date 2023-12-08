# Hot to Run application in Docker container on systemd and manage with systemctl?

### To run commands below you must have docker installed on your system, so let's start:

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
