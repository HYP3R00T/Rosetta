# Ansible Configuration

Ansible looks for the config file in the following order.

- `ANSIBLE_CONFIG` - env variable (if set)
- `ansible.cfg` - in current dir
- `~/ansible.cfg` - in home dir
- `/etc/ansible/ansible.cfg` - default 

For project, I prefer the 2nd option where we define the config file within the project. This way we can keep track of it in git. And if there are multiple ansible config files in different projects, when executed, won't clash with each other. 

## Sample Config File

Thanks to ansible, we can generate a fully commented-out example of the config file. We can redirect the output to a file as well.

```shell
ansible-config init --disabled > ansible.cfg
```

The `--disabled` flag is to ensure that all the lines are commented out.  

---

- [Ansible Configuration Settings](https://docs.ansible.com/ansible/latest/reference_appendices/config.html)
