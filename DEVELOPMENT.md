# Docker

### Build microservice jar files
```shell
mvn clean package -Dmaven.test.skip=true
```

### Build UI
```shell
cd ruoyi-ui
npm install
npm run build:prod
```

### Build docker image
Create `.env` file
```shell
cp .env.example .env
```

Start base container
```shell
cd docker

# copy necessary files
bash copy.sh

# Deploy base image [nginx, mysql, redis, nacos]
bash deploy.sh base
```

**note**: _If Nacos error connection failed, Just restart because mysql has not ready yet_

Start microservice container [ruoyi-gateway, ruoyi-auth, ruoyi-modules-system]
```shell
bash deploy.sh modules
```

Access UI: http://localhost:80