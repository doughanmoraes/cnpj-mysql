## 2026-03-23 - Parameterization of Metadata Insertion Queries
**Vulnerability:** SQL injection vulnerability in metadata insertion (`_referencia` table) due to f-string string interpolation of `dataReferencia` and `qtde_cnpjs`.
**Learning:** Ingestion scripts used f-strings when inserting string values into metadata tables, creating SQL injection risks.
**Prevention:** Always use parameterized SQL queries with bind parameter dictionaries when executing statements with SQLAlchemy `text()`.
