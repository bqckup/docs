# How Bqckup work ?

## Description

The process of backup is a crucial aspect of maintaining the integrity and security of important data. It allows organizations and individuals to create copies of their important files, databases, and other information, and to store them in a separate location. This way, if the original data is lost, damaged, or compromised, the backup can be used to restore it

The backup process works really simple by using YML as the configuration format. This format provides a clear and organized way to specify the details of the backup process, such as the files and databases that need to be backed up, the cloud storage location where the backups will be stored, and any additional options that may be needed.

An example of a YML configuration file for a backup process can be seen below:

{% code title="example1.com.yml" lineNumbers="true" %}
```yaml
bqckup:
  name: example1.com
  path:
    - /etc/bqckup
  database:
    type: 'mysql'
    host: 'localhost'
    port: 3306
    username: 'myusername'
    password: 'mypassword'
    name: 'mydatabase'
  options:
    storage: mystorage
    interval: daily
    retention: 7
    save_locally: no
```
{% endcode %}

{% code title="mystorage.yml" %}
```yaml
s3:
  mystorage:
    bucket: thisnugroho
    access_key_id: 8bc2ce31a67416bc9a60abf126688319
    secret_access_key: bbd2ea387bb08c3adac2b60899f7232f2c2d803eac0a33f6c39b7a35760420e4
    region: auto
    endpoint: https://4fe082a30832ef4bbdb0bb3a0c74123f.r2.cloudflarestorage.com
    primary: yes
```
{% endcode %}

## Preview

<figure><img src="https://bqckup.com/wp-content/uploads/2023/01/Animation.gif" alt=""><figcaption></figcaption></figure>

## Conclusion

The focus is on the overall concept of creating copies of important files, databases, and other information and storing them in a separate location, as well as the use of a configuration file in the format of YML to specify the details of the backup process and the storage of the results of the backup process in SQLite.
