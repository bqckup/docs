---
hidden: true
---

# Add Backup

## YML

Below is an example of the YML configuration for the backups,it should be saved in `/etc/bqckup/sites/config_name.yml`

{% code title="/etc/bqckup/sites/config_name.yml" %}
```yaml
bqckup:
  name: mywebsite
  path:
    - /var/www/html
  exclude:
    - exclude-me #/var/www/html/exclude-me
  options:
    storage: bqckupstorage
    interval: daily
    retention: '7'
    save_locally: no
    provider: s3
    destination: ''
  database:
    host: localhost
    type: mysql
    name: mydatabase
    user: myuser
    password: mypassword.
```
{% endcode %}



{% hint style="info" %}
1. Currently, it only supports Local Storage and S3 Storage.
2. The list that appears in the storage column is the list of storage that is in `/etc/bqckup/config/storages.yml.`
{% endhint %}

{% @mailchimp/mailchimpSubscribe %}
