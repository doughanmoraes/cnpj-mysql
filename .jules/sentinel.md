## 2026-11-02 - SQL Injection in Metadata Table Insertion
**Vulnerability:** Ingestion scripts `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` used Python f-strings to format dynamic values (`dataReferencia` and `qtde_cnpjs`) directly into raw SQL `INSERT` statements when populating the `_referencia` metadata table.
**Learning:** Even internal metadata or summary values derived from file names, user prompts, or query results can introduce SQL injection risks when directly interpolated into SQL strings rather than using parameterized queries.
**Prevention:** Always use parameterized SQL statements with SQLAlchemy `text()` and bind parameter mappings (e.g. `engine.execute(text("INSERT INTO table (col1, col2) VALUES (:param1, :param2)"), {"param1": val1, "param2": val2})`).
