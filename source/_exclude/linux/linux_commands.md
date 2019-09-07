# Linux commands
## grep
grep -r "graphviz"：在当前文件夹（包括子文件夹）搜索包含"graphviz"的文件
grep -rli "graphviz"：只list文件，case insensitive
grep牛逼在还能搜索很多archive和二进制文件比如.class和.jar！

## ps
ps -auwx：查看所有process

## kill
kill -9 187：杀死pid=187的进程

## iptables
iptables是一个防火墙，另有ufw命令可以更简单地管理该防火墙

## ufw
Ubuntu的人性化防火墙配置工具，默认是未启用的

## cp
Copy <source> <destination>