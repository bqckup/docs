# Commands

## Run

This is the command that you use to run the backup, here is how you use it

```
bqckup run
```

It also supports several parameters, to force a backup run even if it’s not on schedule:

```
bqckup run --force
```

To run a backup for a single site:

```
bqckup run --site mywebsite
```

Here, `mywebsite` is the backup name, which you can set in the `name` field inside `/etc/bqckup/sites/domain.yml`
