**FreeBSD**

* [Base Setup](/freebsd/README.md) : Updating, Base rc.conf, Jails, Jail Networking, PF Firewall

** AWS **

#### Intermediate Certs for PositiveSSL

``` 
cat COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt AddTrustExternalCARoot.crt | pbcopy 
```

#### PostGres

Backup a DB for restoring to another host/db:

```
pg_dump -Fc --no-acl --no-owner -h localhost -U {USERNAME} {DB} > backup.dump
```
