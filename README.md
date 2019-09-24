postgresql
==========

Ansible Galaxy role [cesnet.postgresql](https://galaxy.ansible.com/cesnet/postgresql) that installs PostgreSQL 
server from PGDG repository.

Role Variables
--------------

- postgresql_version - version to install, prevents automcatic major version upgrade, default is 11
- postgresql_max_connections - maximum number of allowed connections, default is 150
- postgresql_daily_backup - boolean flag whether to dump DB content into file /var/lib/postgresql/backup.sql.xz, default is True
- postgresl_db_user - when set, creates PostgreSQL user
- postgresl_db_user_password - password for the user
- postgresl_db_name - when set, creates database
- postgres_certificate_file - path to PEM-encoded certificate, used for remote TLS connections (JDBC checks it)
- postgres_certificate_key_file - path to private key
- postgres_certificate_chain_file - path to CA certificate chain 
        
Example Playbook
----------------
```yaml
- hosts: all
  roles:
    - role: cesnet.postgresql
      vars:
        postgresql_version: 11
        postgresql_max_connections: 200
        postgresql_daily_backup: True
        postgresl_db_user: "john"
        postgresl_db_user_password: "X6v38GYN3RxZUYg"
        postgresl_db_name: "cities"
        postgres_certificate_file: "/etc/ssl/localcerts/host_cert.pem"
        postgres_certificate_key_file: "/etc/ssl/localcerts/host_key.pem"
        postgres_certificate_chain_file: "/etc/ssl/localcerts/terena_ssl_ca_3.pem"
```
