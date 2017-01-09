- Put vault_pass_HOST in host_vars/HOST/vault using
```
ansible-vault edit host_vars/HOST/vault
```
- Put vault password in vault_password.txt
- Run playbook
```
ansible-playbook --vault-password-file vault_password.txt -i production site.yml
```
