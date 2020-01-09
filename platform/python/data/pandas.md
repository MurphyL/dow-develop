# Pandas

## 写数据库表（依赖`SQLAlchemy`）

SQLAlchemy用一个字符串表示连接信息：

> 数据库类型+数据库驱动名称://用户名:口令@机器地址:端口号/数据库名

```python
import pandas as pd 
from sqlalchemy import create_engine

engine = create_engine('mysql+pymysql://user:password@localhost/stonetest?charset=utf8')
df = pd.read_sql('emp_master', engine)

# Copy table structure
with engine.connect() as con:
    con.execute('DROP TABLE if exists emp_backup')
    con.execute('CREATE TABLE emp_backup LIKE emp_master;')

df.to_sql('emp_backup', engine, index=False, if_exists='append')
```
## 链接

- [Pandas - User Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html)