# Ansible Facts and Magic Variables

Sometimes, we need to access machine specific variables like the Home directory of the user. In those cases, we can leverage these magic variables.

```yaml
- name: Check if <x> binary exists in ~/.local/bin
  ansible.builtin.stat:
    path: "{{ ansible_env.HOME }}/.local/bin/x"
  register: k3s_binary_check
```

---

- [Discovering variables: facts and magic variables](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_vars_facts.html)
