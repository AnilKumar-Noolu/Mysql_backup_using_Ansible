# Mysql_backup_using_Ansible

This project provides an Ansible playbook to backup MySQL databases on a remote server.

# Pre-requisites:

To use this playbook, you will need:

1. A remote server running MySQL with SSH access
2. Ansible installed on your local machine
3. SSH access to the remote server with sudo privileges
4. AWS CLI installed with S3 full access role attached to it.

After installing all pre-requisites, using the playbook in this repo i.e., main.yml

Execute the playbook using the following command:

```
ansible-playbook main.yml
```

You can find the backup in the following location "/tmp/dump3.sql" and  a new S3 Bucket will be created too with the mysql dump in it.

For creating user and database, we need to enter our password. Instead of passing password directly in the ansible playbook, we have used ansible-vault.

```
ansible-vault create vars/secret.yml
mysql_root_password: mypassword
ansible-playbook playbook.yml --ask-vault-pass
```

In the above way, we are not exposing our passowrds and confidential information anywhere on the playbook.

