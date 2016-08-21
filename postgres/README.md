PostgreSQL
========

### Backing up for restore

```
pg_dump -Fc --no-acl --no-owner -h localhost -U {USERNAME} {DB} > backup.dump
```

### Restoring from a backup

```
pg_restore -h localhost -U {USERNAME} -d {DB}  backup.dump
```
