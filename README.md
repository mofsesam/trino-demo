# Trino demo

Dette repo brukes til å teste ut og eksperimentere med Trino lokalt på egen maskin. Det er ikke ment for produksjon. Enkelhet og ikke sikkerhet er i fokus.

Det er basert på docker filer i dbt-trino repository.

[Følgende "connectorer" er satt opp og har "catalog" i trino:](https://trino.io/docs/current/connector.html)

* delta
* faker
* hive
* iceberg
* memory
* mysql
* postgresql
* system
* tpch

Hvis du har satt opp docker, så trenger du bare gjøre `docker compose up` for å komme igang.

[DBever](https://dbeaver.io/) fungerer godt som client mot Trino. Du kobler opp med host lookalhost, port 8080, username trino og uten passord.

```sql
create table iceberg.default.tiny_customer as
select * from tpch.tiny.customer limit 1000;

select * from iceberg.default.tiny_customer limit 10;
```