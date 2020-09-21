### qdocker安装mysql5.7，且外部能访问

1. docker search mysql，可以看到搜索的结果，这个结果是按照一定的星级评价规则排序的

2. docker pull mysql:5.7.19

3. 具体操作

+ 启动容器

```shell
docker run -id --name=mysql5.7 -p 53306:3306 -v $PWD/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root mysql:5.7.20
```

+ 具体参数

  ```
  -p 3306:3306：将容器的3306端口映射到主机的3306端口；
  
  -v$PWD/mysql:/var/lib/mysql：将主机当前目录下的/mysql挂载到容器的/var/lib/mysql；
  
  -e MYSQL_ROOT_PASSWORD=password：初始化root用户的密码；
  
  --name 给容器命名，mysql5.7
  
  -d 表示容器在后台运行
  
  mysql:5.7.20  docker镜像
  ```

  

4. 如果还是不能连接，是局域网的问题，可以直接进入实例操作

```mysql
mysql> grant all privileges on *.* to root@"%" identified by "password" with grant option;
```

