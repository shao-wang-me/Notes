# Puppet
1. Puppet可以用声明式的语言配置操作系统
2. Puppet manifests: 声明式定义文件
3. Facter：获取系统信息的工具
4. 两种方式实现定义：
	- 直接实现
	- 编译到一个目录系统，然后分发到目标系统（REST API，agent)
5. 开源版和企业版：企业版对节点管理提供GUI、API和命令行工具
6. Server (puppetmaster) - Client (puppet-agent)
7. Agent通过Facter获取系统信息，发送到master，master考虑资源与相互依赖关系，master发送配置信息，agent执行，并返回报告
8. Puppet主要是用Ruby写的
9. Puppet是幂等的（idempotent）：f(f(x)) = f(x)
10. puppet-agent可以在大部分系统上安装，但是puppet platform（puppet-agent, puppetsever, puppetdb, puppetdb-termini）只能在Linux上安装

## 为什么需要IaC (Infrastructure as Code)?
对比shell脚本和CM(Configuration Management)工具脚本:
1. 只需写一点脚本，不用造轮子
2. 不用自己写workflow
3. 一般CM都有UI

## 几个CM工具的对比
CM工具：Puppet, SaltStack, Ansible, Chef
对比标准：规模性、简单搭建、可用性、管理、多平台
1. 几个工具都具有规模性（scalability）
2. 只有Ansible是server only的，其他都是主从式结构，都要安装agent，Ansible直接通过ssh连接nodes，超快
3. 都具有高可用性，要么是多master，要么是主副master
4. sever都是Unix/Linux only，但是节点windows都可以

## 实操tips
1. Windows上安装完puppet-agent之后，可以将/opt/puppetlabs/bin/添加到PATH
2. 在server上管理连接请求（实际上是管理证书签名）
	- 查看：sudo puppetserver ca list
	- 接受：sudo puppetserver ca sign <NAME>，或使用DNS名：sudo puppetserver ca sign (<HOSTNAME> or --all) --allow-dns-alt-names
3. 安装模块：puppet module install ***

## Environment
Environment是Puppet中最高层级，就是一组配置可以配置给很多个节点。一个环境包含Manifest和Modules。
