## 2026-06-30 - Parameterized inserts for metadata table _referencia
**Vulnerability:** SQL injection vulnerability in metadata table insertions in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` via f-string query formatting.
**Learning:** `dataReferencia` is constructed dynamically from filenames extracted during unzipping (`dataReferenciaAux = list(glob.glob(...))[0].split('.')[2]`), making direct interpolation unsafe.
**Prevention:** Always use SQLAlchemy `text()` parameterized queries with bind parameter dictionaries (e.g. `:ref`) for data values.
