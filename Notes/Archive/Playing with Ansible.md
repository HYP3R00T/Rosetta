# Playing with Ansible

Ansible uses SSH to connect to various hosts. For that we need to ensure that the public SSH key of the [[Ansible Controller Node]] is present in each server. Update the `authorized_keys` in all those servers. We can use [[Vagrant]] to achieve that. 

## Basics

- Create a dir `ansible_quickstart`
- Create `inventory.yaml` (We can also create `.ini` file)

```yaml
ungrouped:
  hosts:
    localhost
```

- Check if the file format is correct. It should be if you are using linting. Read more: [[Ansible Lint Setup.md|Ansible Lint Setup.md]].

```shell
ansible-inventory -i inventory.yaml --list
```

- To verify if the hosts are reachable, we ideally go for a simple `ping`. 
    - For localhost: `ansible localhost -m ping`
        - Expected outcome:

            ```
            ❯ ansible localhost -m ping
            localhost | SUCCESS => {
                "changed": false,
                "ping": "pong"
            }
            ```

    - For servers: `ansible <group_name or all> -m ping -i inventory.yaml`

---

- [Ansible Documentation](https://docs.ansible.com/ansible/latest/index.html)
- [How to build your inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html)
- [Implicit ‘localhost’](https://docs.ansible.com/ansible/latest/inventory/implicit_localhost.html)
