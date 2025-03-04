# Cloudflare Deployment Using Poetry

When [creating a new page](https://dash.cloudflare.com/96bcb2b209d735b8fe51bfa9f9df1cf5/workers-and-pages/create/pages) keep the following values.

```text
Build command : poetry run python -m mkdocs build
Build output  : site
```

The default build command is `mkdocs build`. But the issue is that it doesn't use the poetry shell. So, it won't detect that we have the mkdocs installed. 

---

- [Workers and Pages](https://dash.cloudflare.com/96bcb2b209d735b8fe51bfa9f9df1cf5/workers-and-pages)
