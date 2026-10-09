# Samba Active Directory Domain Controller for Docker

A well documented, tried and tested Samba Active Directory Domain Controller that works with the standard Windows management tools; built from scratch using internal DNS and kerberos and not based on existing containers.

## Documentation

Latest documentation available at: [https://nowsci.com/samba-domain/](https://nowsci.com/samba-domain/)

## Optional database backend (inalogy fork)

The image is built on `ubuntu:24.04`. It gets Samba from the Ubuntu noble archive.

Two optional environment variables choose the database backend of a new domain:

- `BACKEND_STORE`: for example `mdb` for LMDB. Samba's default (tdb) is used when it is not set.
- `BACKEND_STORE_SIZE`: the LMDB size in bytes, for example `8589934592`. Used only when `BACKEND_STORE` is set.

They add `--backend-store=...` and `--backend-store-size=...` to `samba-tool domain provision` and `samba-tool domain join`.
With neither variable set, the commands are the same as before. The image still reuses `/etc/samba/external/smb.conf` when it exists.
