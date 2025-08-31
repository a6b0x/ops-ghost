
```sql
CREATE TABLE results WITH (
  connector = 'fluvio',
  endpoint = 'sc:9003',
  topic = 'univ2-factoty-test',
  format = 'json',
  'source.offset' = 'earliest',
  type = 'source'
);
select count(*) from results;
```
```sql
CREATE TABLE test (
   value TEXT
) with (
    type = 'source',
    connector = 'nats',
    servers = 'nats-server:4222',
    subject = 'test',
    format = 'raw_string'
);
select * from test;
select count(*) from test
group by hop(INTERVAL '1' second, INTERVAL '1' minute);

CREATE TABLE test (
   key TEXT,
   step INT
) with (
    type = 'source',
    connector = 'nats',
    servers = 'nats-server:4222',
    subject = 'test',
    format = 'json'
);
select * from test;

``