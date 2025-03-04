# Ansible Inventory

The inventory file can different extensions like `.yaml` or `.ini`. You can leverage `ansible-inventory` command to check the format of the file.

```bash
ansible-inventory -i inventory.yaml --list
```

It is recommended to create an `ansible.cfg` file in the root directory of the project to avoid specifying the inventory file every time.

```ini
# ansible.cfg

[defaults]
inventory = inventory.yaml
```

Now we can verify the inventory using `ansible-inventory --list`.

Any host we mention in the inventory file will at least be a part of 2 groups, even if we don't explicitly create them: `all` and `ungrouped`. If we put a host in a group, then it will belong to that group along with the `all` group. 

For instance, consider the following sample.

```yaml
all:
  hosts:
    localhost:
      ansible_connection: local
```

If we print the graph of the inventory using `ansible-inventory --graph`, we get the following.

```shell
ansible-inventory --graph

@all:
  |--@ungrouped:
  |  |--localhost
```

As we can see, it belongs to both, `ungrouped` as well as `all` groups.

Of course, we can ping the host using ansible and that way we can verify if the host is accessible.

```shell
ansible all -m ping

# [WARNING]: Platform linux on host localhost is using the discovered Python interpreter at /usr/bin/python3.12, but future installation of another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3.12"
    },
    "changed": false,
    "ping": "pong"
}
```

We can see the output which confirms that this host is reachable.

The warning we get is because we are missing the info about interpreter (the python interpreter) in the `ansible.cfg` file.

---

- [Ansible - json schema](https://github.com/ansible/ansible-lint/blob/main/src/ansiblelint/schemas/inventory.json)
- [Building an inventory](https://docs.ansible.com/ansible/latest/getting_started/get_started_inventory.html)
- [How to build your inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html)
