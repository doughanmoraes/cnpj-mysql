## 2026-06-15 - Parameterized SQL Queries in Metadata Insertion
**Vulnerability:** In `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`, SQL insert statements into the `_referencia` metadata table used python f-strings to format variables (`dataReferencia`, `qtde_cnpjs`), introducing SQL injection risk.
**Learning:** `sqlalchemy.text()` parses SQL queries, but passing f-string formatted strings bypasses parameter binding and exposes query parameters to raw SQL interpolation.
**Prevention:** Always pass parameter bindings via dictionaries to `engine.execute(text("..."), {"bind_key": value})`.
