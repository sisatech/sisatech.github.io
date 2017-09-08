# Mac

!> We recommend you install VirtualBox before installing vcli.

Download the osx-amd64 binary from the latest [github release](https://github.com/sisatech/vcli/releases).

Change the permissions of that file to make it executable and copy into a folder, which is in the PATH environment variable.

```bash
chmod 755 ~/Downloads/vcli-X.Y.Z-osx-amd64
cp ~/Downloads/vcli-X.Y.Z-osx-amd64 /usr/local/bin/vcli
```

Verify the installion worked by running a vcli command.
```bash
vcli version
```
