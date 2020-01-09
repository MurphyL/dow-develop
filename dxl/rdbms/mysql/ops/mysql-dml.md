## 数据库管理

```sql
/* 数据库操作 */

-- 显示当当前数据库、前时间、用户名、数据库版本
SELECT database(), now(), user(), version();

-- 创建库
CREATE DATABASE [ IF NOT EXISTS ] 数据库名 数据库选项
数据库选项：
    CHARACTER SET charset_name
    COLLATE collation_name

-- 查看已有库
SHOW DATABASES [ LIKE 'PATTERN' ]

-- 查看当前库信息
SHOW CREATE DATABASE 数据库名


-- 删除库
DROP DATABASE [ IF EXISTS ] 数据库名
```

### 链接

- [吐血整理，1000行MySQL命令，很实用！](https://mp.weixin.qq.com/s/t-DHR6nqUIpqsHX_O4npOA)