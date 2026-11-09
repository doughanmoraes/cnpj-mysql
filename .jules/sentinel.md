## 2026-11-09 - Parameterized Queries for Metadata Tables
**Vulnerability:** SQL injection vulnerability in metadata table (`_referencia`) insertions in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` via f-string interpolation of values like `dataReferencia` and `qtde_cnpjs`.
**Learning:** Ingestion scripts often mix DDL statements (which require raw SQL or identifier interpolation) with DML statements (`INSERT`), leading developers to inadvertently use f-string interpolation for values rather than parameterized bind queries.
**Prevention:** Always use parameterized SQL queries with bind parameters (`:param`) and pass a parameters dictionary to SQLAlchemy's `engine.execute(text(...), params)` for all data manipulation statements.
