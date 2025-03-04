# WSL2 Global Config

We need to create a config file in `%UserProfile%` directory as `.wslconfig`. This will allow us to configure advanced settings like `memory`, `processors`, etc.

For now, I am using it to control the `memory`.

```ini
[wsl2]
memory=6GB 
```

---

- [Main WSL settings](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig)
