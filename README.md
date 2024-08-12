# Demo CI/CD

```
docker compose up -d
```

http://localhost:5000/api/products

```
docker compose down
```


## Image Build & Push
Build Docker image locally and push image to Dockerhub Repository
```
docker login -u sauravm
docker build -t sauravm/demo-cicd:manualBuild_v1 .

# Test Image
# docker run -d -p 5000:5000 sauravm/demo-cicd:manualBuild_v1

docker push sauravm/demo-cicd:manualBuild_v1
```


## Update hosts file
```
sudo vi /etc/hosts

# Append the server entry
127.0.0.1	python-api.local
```

https://python-api.local/api/products

