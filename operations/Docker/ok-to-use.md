### 启动Jenkins
```
docker run -d -p 49001:8080 --add-host repo.eulerproject.io:10.116.122.40 --privileged=true --name jenkins -v $DOCKER_RUNTIME/jenkins:/var/jenkins_home:rw -t cfrost/my-jenkins:0.0.1
```

### 启动MySql
```
docker run --name mysql -p 3306:3306 -v $DOCKER_RUNTIME/mysql/data:/var/lib/mysql -v $DOCKER_RUNTIME/mysql/conf:/etc/mysql/conf.d -d mysql:5.6.35
```