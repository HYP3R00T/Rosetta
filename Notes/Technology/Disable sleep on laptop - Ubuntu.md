# Disable Sleep on Laptop - Ubuntu

To disable the sleep and hibernation, we need to modify `/etc/systemd/sleep.conf`. Edit and make the following changes.

```ini
AllowSuspend=no
AllowHibernation=no
AllowSuspendThenHibernate=no
```

---

- [systemd-sleep.conf](https://manpages.debian.org/testing/systemd/systemd-sleep.conf.5.en.html)
