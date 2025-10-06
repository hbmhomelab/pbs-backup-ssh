## Generate encryption key password

Before running the containers, create a master key by running:

```
docker run --rm -v ./proxmox-backup:/root/.config/proxmox-backup \
  aterfax/pbs-client:latest proxmox-backup-client key create
```

This will generate a random encryption key password that will be listed in the
logs. For example:

```
### IMPORTANT: New client encryption key password: 4x0dkfe5df1XAAd2S46VFnU3n4ixFvE5Piw7SipksJPI ###
```

Add this password to your password manager and make copies of the three files
that have been created in the `proxmox-backup/` directory:

- `encryption-key.json`
- `master-private.pem`
- `master-public.pem`

These files will be needed to restore backups from Proxmox Backup Server if this
installation ever needs to be created again.

Once these files have been secured, edit the `.env` file and add the encryption
key password to the `PBS_ENCRYPTION_PASSWORD` variable.
