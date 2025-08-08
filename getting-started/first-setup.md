# Usage

This documentation will guide you on how to properly set up your **bqckup**.

**Step 1:** Create config for the storages

{% hint style="info" %}
Currently, storage only supports the S3 protocol.
{% endhint %}

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

***

**Step 2:** Create config for your backup

{% hint style="info" %}
There are 2 backup methods: conventional and incremental. The conventional method simply compresses your files into a `.tar.gz` archive and uploads it to the server.
{% endhint %}

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

If it’s incremental, you can append this

```yaml
  incremental:
    enable: yes
    password: mystrongpassword
```

{% hint style="warning" %}
In the background, **bqckup** uses **rustic** for incremental backups, so you need to [install rustic](https://rustic.cli.rs/docs/installation.html) to make the incremental backup work.
{% endhint %}

***

**Step 3:** Run the bqckup

After completing those setups, run **bqckup** using the following command:

```shell
bqckup run
```

***

**Step 4:** Create a cron job to schedule your backup.

If you want it to be executed daily, for example, create a cron job by adding a script inside `/etc/cron.daily/bqckup`.

Command:

```sh
touch /etc/cron.daily/bqckup && chmod +x /etc/cron.daily/bqckup
```

and the content:

{% code title="/etc/cron.daily/bqckup" %}
```sh
/usr/bin/bqckup run >> /var/log/bqckup.log 2>&1
```
{% endcode %}

