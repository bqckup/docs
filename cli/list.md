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

You can get a list of files that were successfully backed up by running this command:

```
bqckup get-list {site_name} --full-id
```

`--full-id`: show the full ID of incremental snapshots

## Generate Link

If you want to download the backup, you can use this command to generate the link:

```
bqckup generate-link {storage_name} {object_path}
```

## Restore

{% hint style="info" %}
Currently, **bqckup** can only restore incremental backups.
{% endhint %}

to perform a restore, use this command:

```shell
bqckup restore {site_name} --snapshot {snapshot_id|default:latest} --target {target_dir|default:directory_source}
```

`site_name`: the name of the site configuration (e.g. domain.com)

`--snapshot`: optional; specify the snapshot ID to restore. If not provided, the latest snapshot will be used.

`--target`: optional; specify the target directory to restore files to. By default, files will be restored to their original source directory.

You can view available snapshot IDs by running:

```
bqckup history --site {site_name}
```

The snapshot ID is shown under the file name field in the history output.
