# PowerShell Commands

- To print pwsh version: `PSVersionTable`
    - For printing specific detail, we can use dot operator: `PSVersionTable.PSVersion`
- Get a list of cmdlet: `Get-Verb`
- List all available cmdlets: `Get-Command`
- Paginated built-in help system: `Get-Help`
    - Update help system: `Update-Help`
- Search any installed cmdlet: `Get-Command`
    - All pwsh default commands uses the format of `Verb + Noun`: `Get-Help`
    - Use `-Verb` to match verb: `Get-Command -Verb Get`
    - Use `-Noun` to match noun: `Get-Command -noun File*`
