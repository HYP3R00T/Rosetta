# Ansible Interpreter Discovery

I got the following warning when I didn't have [[../Technology/Ansible Configuration|Ansible Configuration.md]] properly configured. It didn't have any Python interpreter setting. 

I had to use `pyenv` to install `python3.12` (which also comes with `pip` installed). And then set that as global and installed ansible there. \[NOT Recommended]

```ansible
TASK [Gathering Facts] ***************************************************************************************************************************
[WARNING]: Platform linux on host localhost is using the discovered Python interpreter at /home/hyperoot/.pyenv/shims/python3.12, but future installation of another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
```

---

- [Interpreter Discovery](https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html)
