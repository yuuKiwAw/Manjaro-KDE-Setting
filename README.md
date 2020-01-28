# Manjaro-KDE-配置安装

##配置源

配置国内镜像源
---
sudo pacman-mirrors -i -c China -m rank //更新镜像排名
sudo vim /etc/pacman.d/mirrorlist //查看选择的源
sudo pacman -Syy //更新数据源

设置源
---
sudo vim /etc/pacman.conf

[archlinuxcn]
SigLevel = Optional TrustedOnly
#中科大源
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
#清华源
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

导入GPG Key
---
sudo pacman -Syy //更新数据源
sudo pacman -S archlinuxcn-keyring //安装导入GPG key
sudo pacman -S antergos-keyrin

更新系统
---
sudo pacman -Syu
