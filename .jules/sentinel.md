## 2026-06-30 - SQL Injection in Metadata Table Ingestion

**Vulnerability:** String interpolation (`f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"`) was used when populating metadata table `_referencia` in data ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`).

**Learning:** Unsanitized variables concatenated or f-string interpolated into SQL statements create SQL injection hazards, even if the variable origin is expected to be internal or system-derived.

**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameters (`:param`) for variable data insertions.
