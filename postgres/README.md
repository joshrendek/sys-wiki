PostgreSQL
========

### Backing up for restore

```
pg_dump -Fc --no-acl --no-owner -h localhost -U {USERNAME} {DB} > backup.dump
```
