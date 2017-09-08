# LINUX

!> We recommend you install QEMU before installing vcli.

## Ubuntu

Run the following commands to install vcli with apt.
```bash
curl -s https://packagecloud.io/install/repositories/sisatech/vcli/script.deb.sh | sudo bash && sudo apt install vcli
sudo apt install vcli
```

Verify the installion worked by running a vcli command.
```bash
vcli version
```

## Other
Download the linux-amd64 binary from the latest [github release](https://github.com/sisatech/vcli/releases).

Rename the file to vcli, and move it somewhere on the PATH.

Verify the installion worked by running a vcli command.
```bash
vcli version
```
