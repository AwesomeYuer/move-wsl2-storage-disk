https://medium.com/@carlosrl/why-i-moved-my-ubuntu-distro-wsl2-from-c-to-another-drive-9a29f54e2891

https://learn.microsoft.com/en-us/windows/wsl/basic-commands

https://marquesfernandes.com/en/technology/how-to-move-install-wsl-2-from-disk-c-to-another-disk/

```powershell

ubuntu config --default-user awesomeyuer

```


```dos

wsl --status

wsl --list --online

wsl --list --verbose

wsl --list --all

wsl --shutdown

wsl --export Ubuntu d:\wsl\backup\Ubuntu\Ubuntu.2023-06-27.20-43.tar

wsl --import Ubuntu-22.04.2-LTS-2023-06-28 D:\wsl\Storage\Ubuntu-22.04.2-LTS@2023-06-27 d:\wsl\backup\Ubuntu\Ubuntu.2023-06-27.20-43.tar

Ubuntu-22.04.2-LTS-2023-06-27 config --default-user awesomeyuer

wsl --list --verbose

wsl --list --all

wsl --set-default Ubuntu-22.04.2-LTS-2023-06-27

wsl --shutdown

wsl --unregister Ubuntu

```

WSLg install `microsoft-edge`

```

## Setup
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

sudo install -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/

sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft.gpg] https://packages.microsoft.com/repos/edge stable main" > /etc/apt/sources.list.d/microsoft-edge-stable.list'

sudo rm microsoft.gpg

## Install
sudo apt update

sudo apt install microsoft-edge-stable


# issue
# https://learn.microsoft.com/en-us/answers/questions/695866/wsl-gui-error-at-file-io-posix-cc


# The only thing that worked is installing vcxsrv on windows (run with access control disabled), and add the following in my ~/.bashrc :
# 唯一有效的方法是在 Windows 上安装 vcxsrv （在禁用访问控制的情况下运行），并在我的 ~/.bashrc 中添加以下内容：

# 导出 DISPLAY=$(route.exe print 0.0.0.0 | grep 0.0.0.0 | head -n1 | awk '{ print $4} '):0.0
# export DISPLAY=$(route.exe print 0.0.0.0 | grep 0.0.0.0 | head -n1 | awk '{ print $4} '):0.0

# 导出 LIBGL_ALWAYS_INDIRECT=1
export LIBGL_ALWAYS_INDIRECT=1

```

Add "allow" rule to Windows firewall for WSL2 network #4585

https://github.com/microsoft/WSL/issues/4585

```powershell
#Requires -RunAsAdministrator

New-NetFirewallRule -DisplayName "WSL" -Direction Inbound  -InterfaceAlias "vEthernet (WSL)"  -Action Allow

Set-NetFirewallProfile -Profile Private -DisabledInterfaceAliases "vEthernet (WSL)"

Set-NetFirewallProfile -Profile Public -DisabledInterfaceAliases "vEthernet (WSL)"

```



