## 2024-09-13 - SQL Injection via f-string interpolation in metadata table insertions
**Vulnerability:** Unsanitized variable interpolation in SQL string formatting for inserting metadata into the `_referencia` table in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** Metadata parameters such as `dataReferencia` were formatted using Python f-strings inside `text()`, creating SQL injection risks if variables contain untrusted input.
**Prevention:** Always use SQLAlchemy `text()` with bind parameter dictionaries (e.g., `:ref` and `:val`) for executing parameterized queries.
