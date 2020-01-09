## 使用Docker创建MySQL服务

```sh
docker run --rm -itd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mysql mysql
```

```sh
docker exec -it mysql-inst sh -c 'exec mysql -uroot -pmysql'
```