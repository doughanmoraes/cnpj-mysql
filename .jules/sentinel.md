## 2026-03-31 - SQL Injection in _referencia Metadata Insertion
**Vulnerability:** SQL injection hazard caused by f-string interpolation of `dataReferencia` and `qtde_cnpjs` values into SQL INSERT queries for the `_referencia` metadata table.
**Learning:** SQL queries built via f-strings are prone to injection risks if variables contain untrusted input.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameters (`:val`).
