## 2026-06-25 - SQL Injection in _referencia Table Metadata Ingestion
**Vulnerability:** Raw f-string interpolation was used in SQL `INSERT` statements when recording `dataReferencia` and `qtde_cnpjs` in `_referencia` metadata table.
**Learning:** Even internal metadata or processed variable strings inserted via `engine.execute(text(f"..."))` pose SQL injection risks if input values or parsed data contain single quotes or malicious SQL fragments.
**Prevention:** Always use SQLAlchemy bind parameters with `text(...)` and parameter dictionaries (e.g. `{"val": value}`) rather than Python f-strings or string concatenation.
