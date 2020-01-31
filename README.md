# Manjaro-KDE-配置安装

## 配置源

### 配置国内镜像源

```
sudo pacman-mirrors -i -c China -m rank //更新镜像排名
sudo vim /etc/pacman.d/mirrorlist //查看选择的源
sudo pacman -Syy //更新数据源
```

### 设置源
```
sudo vim /etc/pacman.conf

[archlinuxcn]
SigLevel = Optional TrustedOnly
#中科大源
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
#清华源
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
### 导入GPG Key
```
sudo pacman -Syy //更新数据源
sudo pacman -S archlinuxcn-keyring //安装导入GPG key
sudo pacman -S antergos-keyrin
```
### 更新系统
```
sudo pacman -Syu
```

## 安装zsh
```
sudo pacman -S zsh
cat /etc/shells //查看本机有哪几种shell
chsh -s /bin/zsh
```
### 安装oh-my-zsh配置文件
```
via curl
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

或者 

via wget
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
### 替换zsh的配置文件为oh-my-zsh
```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
### 主题以及插件
```
nano ~/.zshrc //配置文件
ZSH_THEME="agnoster" //主题

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting //高亮插件

git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions //自动补全

plugins=(
  git
  zsh-syntax-highlighting
  zsh-autosuggestions
)
```
### 刷新配置
```
source ~/.zshrc
```
## 配置搜狗拼音

### 安装fcitx输入法管理器
```
sudo pacman -S fcitx-im     //全部安装
sudo pacman -S fcitx-qt4    //搜狗拼音只支持qt4
sudo pacman -S fcitx-configtool     //图形化配置工具
sudo pacman -S fcitx-sogoupinyin
```
### 配置文件
```
nano ~/.xprofile

export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=”@im=fcitx”
```

