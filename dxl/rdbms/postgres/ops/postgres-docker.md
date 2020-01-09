## 使用Docker创建Postgres服务

```sh
# 安装PostgreSQL
docker pull postgres

# 运行
docker run --name postgres1 -e POSTGRES_PASSWORD=password -p 54321:5432 -d postgres

# 客户端访问
psql -U postgres -h 192.168.100.172 -p 54321
```