# Fzf Colors

In Windows Terminal, 24 bit colors are not supported. So, it's wise to use ANSI colors for `fzf`

```shell
export FZF_DEFAULT_OPTS=" \
--color=fg:15,bg:0,hl:14 \
--color=fg+:15,bg+:0,hl+:12 \
--color=info:10,prompt:9,pointer:13 \
--color=marker:10,spinner:13,header:6 \
--multi"
```

This is `Mocha` color scheme

---

- [GitHub Issue: -color is not producing colors in Terminal.app](https://github.com/junegunn/fzf/issues/3151#issuecomment-1413292042)
