# Ansible Playbook Variables

These are the variables that we are creating. There are two (not really) ways to keep the vars. 

- Keep the vars in `vars/main.yml` within a role.
- Keep the vars in a single `vars.yml` file in the root of the project.
    - In `playbook.yml` add the following

        ```yaml
        - name: Ansible playbook
          vars_files:
            - vars.yml
        ```

---

- [Variable precedence: Where should I put a variable?](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable)
- [Using Variables](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html)
