# Linux package management

## 升级系统
do-release-upgrade

## Apt
apt使用Ubuntu的APT (Advanced Packaging Tool)

apt help
sudo apt update: 更新列表
sudo apt upgrade: 升级软件
sudo apt install ***
sudo apt remove ***
apt list --upgradable: 可以升级的软件

## Aptitude
Aptitude同样使用APT, 本质上是一个menu-driven, text-based界面

sudo aptitude: 显示菜单式界面
帮助: https://help.ubuntu.com/lts/serverguide/aptitude.html.en

亦可作command-line工具:
sudo aptitude install ***
sudo aptitude remove ***
