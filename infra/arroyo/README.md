
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