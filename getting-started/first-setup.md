# Usage

## Create Storage Config

Storage Config Stored in `/etc/bqckup/config/storage.yml`

```yaml
storages:
  ojtbackup:
    bucket: ${BUCKET_NAME}
    access_key_id: ${ACCESS_KEY}
    secret_access_key: ${SECRET_KEY}
    region: ${REGION}
    endpoint: ${ENDPOINT_URL}
    primary: yes
```

There is also an option for remote storage, which you can [read it here](../storages/remote-storage.md).

## Create Bqckup Config

There are two backup methods: conventional and incremental. The conventional method simply compresses your files into a `.tar.gz` archive and uploads it to the server.

The configuration can be created in `/etc/bqckup/sites/your-config-name.yml`.

{% code title="/etc/bqckup/sites/mywebsite.yml" %}
```yaml
bqckup:
  name: ${name}
  path:
    - ${path}
  database:
    type: mysql #Currently only support mysql
    host: localhost
    port: 3306
    user: ${db_user}
    password: ${db_password}
    name: ${db_name}
  options:
    storage: ${storage_name} #can be found at /etc/bqckup/config/storages.yml
    interval: daily # daily | weekly | monthly
    retention: 7
    save_locally: no # It will not delete your backup after it has been uploaded.
    save_locally_path: /home/user/_backups
    provider: s3
```
{% endcode %}

if it's incremental you can append this

```yaml
  incremental:
    enable: yes
    password: mystrongpassword
```

{% hint style="warning" %}
In the background, **bqckup** uses **rustic** for incremental backups, so you need to [install rustic](https://rustic.cli.rs/docs/installation.html) to make the incremental backup work.
{% endhint %}

## Run Bqckup

After completing those setups, run **bqckup** using the following command:

```shell
bqckup run
```

You can then set up a cron job to schedule it. Typically, I create a file named `bqckup` inside `/etc/cron.daily`:

command to create cron:

```sh
touch /etc/cron.daily/bqckup && chmod +x /etc/cron.daily/bqckup
```

and it's content:

{% code title="/etc/cron.daily/bqckup" %}
```sh
/usr/bin/bqckup run >> /var/log/bqckup.log 2>&1
```
{% endcode %}

