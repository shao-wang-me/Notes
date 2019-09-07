# Bamboo

Bamboo is a CI (continuous integration) tool

## 原理
1. 从代码仓库获取代码
2. 用Maven、MSBuild等构建工具进行构建
3. 存储构建物

## 重要文件夹和文件
1. 安装文件夹
2. home文件夹：在atlassian-bamboo/WEB-INF/classes/bamboo-init.properties中定义
3. bin/start-bamboo.sh/bat：Bamboo启动脚本
4. scripts/Triggers：触发器脚本
5. logs/：日志，如果使用Windows安装器安装的，则在