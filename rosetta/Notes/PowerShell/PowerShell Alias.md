---
tags:
  - pwsh
date: 2024-11-26
---

# PowerShell Alias

- Open the profile using `code $PROFILE`. 
- Create a new function. 

```shell
# Functions
function myfunc {
    Set-Location -Path "C:\add\path\here"
}
```

- Create a new alias and set it for this function.

```shell
# Aliases
New-Alias cdr cd_into_rosetta
```

## Note:

- Aliases created by using `New-Alias` are not saved after you exit the session or close PowerShell.
- Either use `Export-Alias` cmdlet to save alias information or use `Set-Alias`.

---

### References:

- [Set-Alias](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/set-alias)
