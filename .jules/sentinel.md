## 2026-06-30 - Parameterized SQL queries for metadata insertion
**Vulnerability:** String interpolation (f-strings) in SQL queries when populating the `_referencia` metadata table.
**Learning:** Even internal metadata variables or dates extracted from filenames can present SQL injection risks if not sanitized or parameterized.
**Prevention:** Always use SQLAlchemy `text()` with bind parameters (`:param`) and pass parameter dictionaries when executing SQL statements.
