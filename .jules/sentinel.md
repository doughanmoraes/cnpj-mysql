## 2026-06-30 - SQL Injection in Metadata Table Population

**Vulnerability:** In `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`, SQL insert statements populating the `_referencia` metadata table were constructed using f-strings interpolating `dataReferencia` and `qtde_cnpjs`. Because `dataReferencia` is sourced from external filenames or user input, unescaped interpolation presents a SQL injection vulnerability.

**Learning:** Data pipeline scripts often use parameterized queries for core records via ORM or bulk operations (like `to_sql`), but developers sometimes fall back to raw string interpolation for auxiliary or metadata tables. Even internal metadata queries must strictly utilize query parameters.

**Prevention:** Use SQLAlchemy `text()` with bind parameter mappings (e.g., `engine.execute(text("INSERT INTO table (col1, col2) VALUES (:val1, :val2)"), {"val1": ..., "val2": ...})`) instead of format strings or string concatenation.
