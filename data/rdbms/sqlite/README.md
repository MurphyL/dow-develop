
## upsert

```sql
INSERT INTO visits (ip, hits)
VALUES ('127.0.0.1', 1)
ON CONFLICT(ip) DO UPDATE SET hits = hits + 1;
```

## 链接

- [SQLite: Functions - Listed by Category](https://www.techonthenet.com/sqlite/functions/index.php)
- [SQL As Understood By SQLite](https://www.techonthenet.com/sqlite/functions/index.php)