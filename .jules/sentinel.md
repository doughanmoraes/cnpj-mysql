## 2026-06-01 - Parameterizing Metadata Queries in Database Scripts
**Vulnerability:** Raw f-strings were used to interpolate runtime values (`dataReferencia` and `qtde_cnpjs`) directly into SQL `INSERT` statements for the `_referencia` metadata table in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`, presenting SQL injection risks.
**Learning:** In scripts executing bulk data migrations or DDL/DML, dynamic SQL queries can inadvertently introduce SQL injection when passing script variables into `text(...)` blocks instead of using bind parameters.
**Prevention:** Always use SQLAlchemy bind parameter dictionaries (e.g. `:ref`, `:val`) passed to `engine.execute(...)` when inserting values into SQL queries rather than f-string or string formatting.
