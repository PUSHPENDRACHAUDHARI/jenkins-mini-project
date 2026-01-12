<<<<<<< HEAD
# demo-mvn-docker-jenkins

Small DevOps-ready demo project:
- Spring Boot (Java 17)
- Maven build
- Dockerfile + docker-compose
- Jenkins CI/CD pipeline (Jenkinsfile)

## Run locally (Docker)
```bash
docker compose up -d --build
curl http://localhost:8080
```

## Jenkins setup (Docker)
```bash
docker run -d \
  --name jenkins \
  -p 8081:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

Open:
http://<VPS-IP>:8081

Get admin password:
```bash
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Jenkins Pipeline
Create a Pipeline job:
- Pipeline script from SCM
- Git repo: your repo URL
- Script path: Jenkinsfile
=======
# jenkins-mini-project
>>>>>>> cfb2df0de3d74fdea631c52fd1ad81120aa5cfe3
