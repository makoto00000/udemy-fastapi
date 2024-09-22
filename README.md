# FastAPIの基礎

## alembic

マイグレーションツール。

インストール

```shell
pip install alembic psycopg2-binary
```

初期設定

```shell
alembic init migrations
```

`alembic.ini`の`sqlalchemy.url`を変更

```ini
sqlalchemy.url = postgresql://fastapiuser:fastapipass@postgres:5432/fleamarket
```

`env.py`の`target_metadata`を変更

```python
from models import Base
.
.
.
target_metadata = Base.metadata
```

マイグレーションファイルを作成

```shell
alembic revision --autogenerate -m "Create items table"
```

データベースに反映

```shell
alembic upgrade head
```
