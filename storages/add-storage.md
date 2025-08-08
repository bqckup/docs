---
hidden: true
---

# Add Storage



{% hint style="info" %}
Currently, it's only supports S3 Object Storage.
{% endhint %}

To add a new storage, you simply need to edit the file `/etc/backup/config/storages.yml`.

the `storages.yml` should be look like this

```yaml
storages:
  # mystorage is the name you can replace it whatever you want
  mystorage:
    bucket: mystoragebucket
    access_key_id: mystorageaccesskey
    secret_access_key: mystoragesecretkey
    region: mystorageregion
    endpoint: https://mystorage.endpoint
    primary: yes
  # mystorage2 is the name you can replace it whatever you want
  mystorage2: 
    bucket: mystorage2bucket
    access_key_id: mystorage2access
    secret_access_key: mystorage2secretkey
    region: mystorage2region
    endpoint: https://mystorage2.endpoint
    primary: no
  # if you had another storage you can put it in here, and so on
  mystorage3:
      ...
# This file is created with bqckup.com. Tool for create seamless bqckup for your website
```

If you have three storage options, you can add them to the configuration file

{% @mailchimp/mailchimpSubscribe %}
