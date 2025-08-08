# Remote Storage

The _remote storage_ feature is a mechanism where storage credentials are obtained from an external source.

The configuration that needs to be adjusted is located at `/etc/bqckup/config/storages.yml`.

```yaml
storages:
  dummy:
    bucket: dummy
    primary: yes
    remote_url: https://domain.com/api/get?token=894211610151115239
```

The response format is as follows.

```json
{
    "bucket": "string"
    "access_key_id": "string",
    "secret_access_key": "string",
    "endpoint": "string",
    "region": "string"
}
```
