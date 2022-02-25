YML

```yaml
version: "3" #指定 docker-compose.yml 文件的写法格式
services: #定义的服务，每个容器为一个服务，可定义多个
  mysql-db:
    container_name: mysql # 指定容器的名称
    image: registry.cn-shenzhen.aliyuncs.com/tyssq/mysql:8.0 # 指定镜像和版本
    ports: #端口映射 "宿主机端口:容器暴露端口" 仅指定容器端口时，宿主机将会随机选择端口 
      - "3306:3306" 
    environment: #环境变量
      MYSQL_ROOT_PASSWORD: root
      MYSQL_ROOT_HOST: ${MYSQL_ROOT_HOST}
      TZ: Asia/Shanghai # 指定时区
    volumes: #卷挂载路径 "宿主:容器"
      - "./data:/var/lib/mysql" # 挂载数据目录
      - "./config:/etc/mysql/conf.d" # 挂载配置文件目录

```

CLI

```shell
#启动服务 
docker-compose start 
#停止服务 
docker-compose stop
#重启服务
docker-compose restart
#版本
docker-compose -v
#查看运行容器
docker-compose ps
#容器输出日志
docker-compose logs
#启动 -d后台运行
docker-compose up -d
```