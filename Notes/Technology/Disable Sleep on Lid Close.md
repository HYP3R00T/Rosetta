# Disable Sleep on Lid Close

How laptop behave when we press the power button or close the lip can be controlled with a file in the `systemd` dir called `logind.conf`.

- Modify the file and add/uncomment the following.

    ```shell
    HandleLidSwitch=ignore
    HandleLidSwitchExternalPower=ignore
    HandleLidSwitchDocked=ignore
    ```

- Then restart the service: `sudo systemctl restart systemd-logind`

---

- [logind.conf(5) — Linux manual page](https://www.man7.org/linux/man-pages/man5/logind.conf.5.html)
- [manpages.debian.org/testing/systemd/logind.conf.5.en](https://manpages.debian.org/testing/systemd/logind.conf.5.en.html)
