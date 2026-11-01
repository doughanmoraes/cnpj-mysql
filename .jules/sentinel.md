## 2026-11-01 - SQL Injection via String Interpolation in Metadata Inserts
**Vulnerability:** Inserting metadata values (`dataReferencia` and `qtde_cnpjs`) into the `_referencia` table using python f-string interpolation inside `engine.execute(text(f"..."))` created a potential SQL injection vulnerability if external or unexpected input was present.
**Learning:** Even though `text()` from SQLAlchemy was used, wrapping an f-string inside `text(...)` negates parameterization safety unless bind parameters are passed explicitly as a dictionary.
**Prevention:** Always use bind parameters (e.g., `:referencia`, `:valor`) with SQLAlchemy `text()` and supply arguments via a parameter dictionary.
