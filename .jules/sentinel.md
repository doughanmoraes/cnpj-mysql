# Sentinel Security Journal

## 2026-06-15 - SQL Injection in Metadata Table Insertions
**Vulnerability:** String interpolation (`f-string`) was used when inserting dynamic `dataReferencia` and `qtde_cnpjs` values into the `_referencia` metadata table in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** Database metadata table insertions were using string formatting rather than parameter bindings, leaving the queries vulnerable to SQL injection if input data or filenames contained untrusted input or single quotes.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameter dictionaries (e.g., `:ref` and `:val`) when inserting variables into database tables.
