# Sentinel's Journal - Critical Security Learnings

This journal documents critical security learnings, patterns, and insights discovered while guarding this codebase.

## 2026-03-30 - SQL Injection via String Interpolation in Metadata Insertion
**Vulnerability:** Inserting runtime metadata (`dataReferencia`, `qtde_cnpjs`) into the `_referencia` table using Python f-strings in SQL statements (`insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')`).
**Learning:** Even internal metadata or date values parsed from external file paths can introduce SQL injection risks or fail on unexpected input formats if directly concatenated or interpolated into SQL statements.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameter dictionaries (`:ref`, `:val`) rather than string interpolation or concatenation.
