## 2026-03-23 - Parameterized Queries for Database Metadata Tables
**Vulnerability:** String interpolation (`f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"`) was used in both `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` to insert metadata extracted from filenames or external inputs into the `_referencia` table, introducing SQL injection risks.
**Learning:** Even auxiliary/metadata insertions where variables appear to be derived from file extensions or counters are prone to SQL injection if filenames or variables are manipulated or malformed.
**Prevention:** Always use SQLAlchemy `text()` with bind parameters (`:param`) and pass a parameters dictionary to `engine.execute(...)` instead of Python f-strings.
