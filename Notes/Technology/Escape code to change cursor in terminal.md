# Escape Code to Change Cursor in Terminal

There is a special escape sequence that can set the cursor shape. 

```shell
echo -e "\e[6 q" # vertical line
```

- `\e`: Escape character (also written as `\033`).
- `[6 q`: Escape sequence to set the cursor shape.
    - `0 q`: Blinking block
    - `1 q`: Blinking block (default)
    - `2 q`: Steady block
    - `3 q`: Blinking underline
    - `4 q`: Steady underline
    - `5 q`: Blinking bar (vertical line)
    - `6 q`: Steady bar (vertical line)

---

- [XTerm Control Sequences](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html)
