## 2026-06-30 - SQL Injection in Metadata Table Ingestion
**Vulnerability:** The metadata table `_referencia` insertion in both `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` used string f-string interpolation for variables `dataReferencia` and `qtde_cnpjs`, leaving the database vulnerable to SQL injection if file contents/metadata were manipulated.
**Learning:** Legacy database insertion code constructed dynamic SQL queries with f-strings even when using SQLAlchemy `text()`.
**Prevention:** Always parameterize SQL queries in SQLAlchemy using bind variables (e.g., `:ref`, `:val`) and pass arguments in dictionary parameters to `engine.execute(...)`.
