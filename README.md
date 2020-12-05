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
### 安装网易云音乐
```
sudo pacman -S netease-cloud-music
```
### GFWlist
```
https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt
```
### Anaconda配置
```
yay -S anaconda
source /opt/anaconda/bin/active root

# 在 ~/.bashrc 中添加
export PATH=/opt/anaconda/bin:$PATH
source /opt/anaconda/bin/activate root

# 关于 zsh，打开 ~/.zshrc
vim ~/.zshrc
export PATH="/opt/anaconda/bin:$PATH"
source ~/.zshrc

# 配置镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

# 创建环境
conda create -n py38 python=3.8
# 删除环境
conda remove -n py38 --all
# 查看已有环境
conda info -e

# 查看当前环境下已安装的包
conda list

# 查看某个指定环境的已安装包
conda list -n python34

# 查找package信息
conda search numpy

# 安装package
conda install -n python34 numpy
# 如果不用-n指定环境名称，则被安装在当前活跃环境
# 也可以通过-c指定通过某个channel安装

# 更新package
conda update -n python34 numpy

# 删除package
conda remove -n python34 numpy

# 更新conda，保持conda最新
conda update conda

# 更新anaconda
conda update anaconda

# 更新python
conda update python
# 假设当前环境是python 3.4, conda会将python升级为3.4.x系列的当前最新版本
```
