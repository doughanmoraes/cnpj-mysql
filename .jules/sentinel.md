## 2026-06-25 - Metadata Table SQL Injection via f-strings
**Vulnerability:** Inserting `dataReferencia` and `qtde_cnpjs` values into `_referencia` metadata table using Python f-string query formatting.
**Learning:** Legacy ingestion scripts relied on string interpolation for inserting metadata string values into SQL statements.
**Prevention:** Always use SQLAlchemy parameterized queries (`text("INSERT ... (:bind1, :bind2)")` with parameter dicts) for inserting dynamic values.
