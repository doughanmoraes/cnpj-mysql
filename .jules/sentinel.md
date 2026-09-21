## 2026-06-18 - Parameterize Metadata Table Inserts
**Vulnerability:** Raw string formatting (`f"insert into _referencia ... '{dataReferencia}'"`) allowed potential SQL injection in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** Variables populated dynamically from metadata strings in raw file names or DB queries were passed to SQL statements via f-strings rather than bind parameters.
**Prevention:** Always use SQLAlchemy bound parameters (e.g., `text("... values (:ref, :val)")` with parameter dictionaries) even for internal script variables.
