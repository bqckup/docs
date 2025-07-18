---
description: Fixing a Corrupted Rustic Repository or Backup Incremental Error
---

# Fixing a Corrupted Incremental Backup

## Common Issues

Some common issues that can occur in a Rustic repository include:

* Corrupted index files
* Damaged snapshots
* Malformed data packs or packs not referenced in the index (often caused by an abrupt interruption during backup)

## Consequences

* **Corrupted index**: This can usually be repaired.
* **Corrupted snapshot**: If a snapshot is damaged, it’s very likely that the associated data cannot be restored.
* **Broken packs**: These need to be removed. After that, a new backup should be performed to ensure repository integrity.

## How to Handle Corrupted Rustic Repository Issues

### Check The Repository

Run the following command to check the integrity of the Rustic repository:

```sh
rustic check
```

### Attempt to Repair

If the check reports issues with the index or snapshots, try to repair them using:

```
rustic repair index
rustic repair snapshots
```

### Re-run the Backup

After fixing the issues, re-run the backup to ensure the repository is up to date and consistent:

```
bqckup run --site {domain_name} --force
```

For more detailed troubleshooting steps, refer to the [official Restic documentation](https://restic.readthedocs.io/en/latest/077_troubleshooting.html).
