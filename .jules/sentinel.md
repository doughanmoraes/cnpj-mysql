## 2026-06-03 - Parameterize SQL queries for metadata insertions
**Vulnerability:** In `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`, metadata tables like `_referencia` were historically populated using f-string interpolation for variables like `dataReferencia`, creating SQL injection risks.
**Learning:** Even internal metadata or summary counts must be parameterized when inserted into the database.
**Prevention:** Always use SQLAlchemy `text()` with bind parameters (`:ref`, `:val`) and dictionary parameters rather than Python f-strings or string formatters when constructing SQL statements.
