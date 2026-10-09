## 2026-06-18 - Parameterized Queries for Metadata Inserts
**Vulnerability:** SQL injection vulnerability when inserting metadata values (`dataReferencia` and `qtde_cnpjs`) into the `_referencia` table using Python f-string interpolation inside `engine.execute(text(...))`.
**Learning:** Even internal metadata or dynamically derived strings in SQL ETL pipelines can become injection vectors if unescaped or sourced from untrusted file headers or environment values.
**Prevention:** Always pass bind parameters as dictionaries to `engine.execute(text("... :param ..."), {"param": val})` rather than string interpolation or f-strings.
