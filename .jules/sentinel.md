# Sentinel Security Journal

## 2026-03-23 - Parameterized Queries for Database Metadata
**Vulnerability:** The data ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`) inserted reference metadata into `_referencia` using Python f-string interpolation (`engine.execute(text(f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"))`), introducing SQL injection vulnerabilities if variables like `dataReferencia` contain unexpected characters.
**Learning:** Even internal metadata values derived from extracted file names or user prompts must be treated as untrusted inputs and inserted via parameterized queries.
**Prevention:** Always use parameterized SQL queries with bind parameters (`engine.execute(text("... (:ref, :val)"), {'ref': ..., 'val': ...})`) rather than string or f-string interpolation.
