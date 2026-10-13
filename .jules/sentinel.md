## 2026-06-30 - Parameterize SQL queries for metadata insertions
**Vulnerability:** String interpolation (f-strings) in SQL INSERT statements for `_referencia` metadata table in ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`) created potential SQL injection risks if input data contained SQL control characters.
**Learning:** Even internal metadata or reference dates dynamically extracted or formatted should use parameterized queries rather than string formatting.
**Prevention:** Always use SQLAlchemy `text()` with bind parameter dictionaries (e.g. `:ref` and `:val`) instead of f-strings for SQL operations.
