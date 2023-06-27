https://medium.com/@carlosrl/why-i-moved-my-ubuntu-distro-wsl2-from-c-to-another-drive-9a29f54e2891

https://learn.microsoft.com/en-us/windows/wsl/basic-commands

```sh

wsl --status

wsl --list --online

wsl --list --verbose

wsl --list --all

wsl --shutdown

wsl --export Ubuntu d:\wsl\backup\Ubuntu\Ubuntu.2023-06-27.18-30.tar

wsl --import Ubuntu-22.04.2-LTS-2023-06-27 D:\wsl\Storage\Ubuntu-22.04.2-LTS@2023-06-27 d:\wsl\backup\Ubuntu\Ubuntu.2023-06-27.18-30.tar

wsl --list --verbose

wsl --list --all

wsl --set-default Ubuntu-22.04.2-LTS-2023-06-27

wsl --shutdown

wsl --unregister Ubuntu

```

https://marquesfernandes.com/en/technology/how-to-move-install-wsl-2-from-disk-c-to-another-disk/