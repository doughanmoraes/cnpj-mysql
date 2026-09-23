## 2026-03-31 - SQL Injection in Metadata Table Ingestion

**Vulnerability:**
Inserting metadata (`dataReferencia` and `qtde_cnpjs`) into `_referencia` table used Python f-string query formatting rather than parameterized bind parameters.

**Learning:**
String interpolation in SQL queries, even for internal or parsed variables, creates potential SQL injection points if input data or filenames are manipulated.

**Prevention:**
Always use parameterized SQL queries with SQLAlchemy `text()` and pass variables via parameter dictionaries (`:ref` and `:val`).
