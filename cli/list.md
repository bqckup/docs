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

Here, `mywebsite` is the backup name, which you can set in the `name` field inside `/etc/bqckup/sites/domain.yml`\


You can also choose to run either an incremental or a full backup using this command.

```
bqckup run --site mywebstite --incremental | --full
```

## History

The backup history can be viewed using the following command:

```
bqckup history --site {site_name}
```

`site_name` also refers to the value of `name` inside `/etc/bqckup/sites/domain.yml`.

## Get List

Coming soon

## Generate Link

Coming soon

## Restore

Coming soon
