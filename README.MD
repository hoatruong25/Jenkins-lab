## JENKINS RESEARCH PROJECT
### Source base: 
Link youtube: [Learn Jenkins! Complete Jenkins Course - Zero to Hero](https://www.youtube.com/watch?v=6YZvp2GwT0A)

Link github: [jenkins-101](https://github.com/devopsjourney1/jenkins-101/blob/master/Dockerfile)


### Step by step
1. Build images
```
docker build -t myjenkins-blueocean:2.492.1 .
```

2. Create docker network for Jenkins
```
docker network create jenkins
```

3. Run Container
```
docker run --name jenkins-blueocean --restart=on-failure --detach `
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 `
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 `
  --volume jenkins-data:/var/jenkins_home `
  --volume jenkins-docker-certs:/certs/client:ro `
  --publish 8080:8080 --publish 50000:50000 myjenkins-blueocean:2.492.1
```

4. Create Password for Jenkins
```
docker exec jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword
```