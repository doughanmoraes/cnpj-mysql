## 2026-06-18 - Parameterized Queries in CNPJ Reference Ingestion Table
**Vulnerability:** In `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`, insertion into the `_referencia` metadata table used python f-strings (`insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')`), which poses an SQL injection risk if metadata variable values contain unescaped single quotes or user input.
**Learning:** Metadata/reference tables populated dynamically during ingestion were previously overlooked for parameterized query safety because they were thought to only contain internal dates or integer counts.
**Prevention:** Always use SQLAlchemy `text()` bind parameters (e.g., `:ref` and `:val`) passed via a dictionary mapping even for internal metadata variables.
