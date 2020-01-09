## JDBC - ACID && 事务隔离

### 事务隔离级别设置

```java
conn.setTransactionIsolation(Connection.TRANSACTION_SERIALIZABLE);
```