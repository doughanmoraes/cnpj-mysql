## 2026-03-30 - SQL Injection in Database Reference Table Insertions
**Vulnerability:** The database ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`) inserted metadata into the `_referencia` table using Python f-string interpolation (`f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"`), exposing the application to SQL injection vulnerabilities if inputs contained unsanitized quotes or SQL syntax.
**Learning:** Ingestion scripts that populate metadata tables often use string formatting instead of ORM or parameterized execution out of convenience, bypassing database escaping mechanisms.
**Prevention:** Always use parameterized SQL queries with bind parameters (`text("... :ref ..."), {"ref": ...}`) even for metadata table insertions.
