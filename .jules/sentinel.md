# Sentinel's Journal

## 2026-10-31 - SQL Injection in Database Metadata Tracking
**Vulnerability:** Inserting pipeline execution metadata (`dataReferencia` and `qtde_cnpjs`) into the `_referencia` table used raw Python f-strings with `engine.execute(text(f"insert into _referencia ... values ('{val}')"))`. In addition, `dados_cnpj_postgres.py` contained a hardcoded default password placeholder (`senha`).
**Learning:** Even internal metadata logs or extraction summary tables are vulnerable to SQL injection if variables parsed from file system paths, filenames, or user inputs are concatenated directly into SQL queries rather than using parameterized query execution.
**Prevention:** Always use SQLAlchemy parameter binding with dictionaries (e.g., `engine.execute(text("insert into ... values (:ref, :val)"), {"ref": ..., "val": ...})`) even for simple administrative or metadata insert statements.
