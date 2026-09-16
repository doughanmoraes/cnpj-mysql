## 2026-06-25 - SQL Injection in Metadata Table Population
**Vulnerability:** SQL injection risk in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` where SQL queries inserted data into `_referencia` using Python f-strings f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')".
**Learning:** Raw f-strings were used for final status metadata insertion because the values (`dataReferencia` and `qtde_cnpjs`) were internally generated variables rather than user form inputs, creating a false sense of security.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` placeholders and bind parameter dictionaries even for internal metadata variables.
