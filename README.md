### hcf-upgrade

[![GitHub release](https://img.shields.io/github/release/monlor/hcf-upgrade.svg)](https://github.com/monlor/hcf-upgrade/releases)

一款Rancher环境升级脚本，将目标环境的镜像版本同步升级到来源环境的版本，升级前会对比apollo配置信息，确认后才执行升级动作

### 安装教程

#### 【推荐】brew安装（[brew](https://brew.sh/index_zh-cn)支持WSL/Linux/Mac）

```
➜ brew tap monlor/taps
➜ brew install hcf-upgrade
➜ brew upgrade hcf-upgrade # 脚本更新命令
```

### 帮助

```
Upgrade HCF project from source env to target env
Version: 0.0.1
Usage: hcfup -c [config file]
Options:
	-c [config file]		
	-h 			show help info
	-v 			show version

Config File Example:
	source_rancher_url=https://22.22.22.22:9043/k8s/clusters/22
	source_rancher_token=token-22
	source_rancher_project=22:22
	source_rancher_namespace=default
	source_apollo_url=http://22.22.22.22:8180
	source_apollo_namespace=common,application
	source_apollo_cluster=xxxx
	target_rancher_url=https://11.11.11.11:9043/k8s/clusters/11
	target_rancher_token=token-11
	target_rancher_project=11:11
	target_rancher_namespace=default
	target_apollo_url=http://11.11.11.11:8180
	target_apollo_namespace=common,application
	target_apollo_cluster=default
	# 跳过工作负载升级的应用（正则）
	skip_workload=rzh\|network-utils
	# 跳过apollo配置检查的应用（正则）
	skip_apollo=web-app1

Use Example:
	hcfup -c config.properties
```

### 使用姿势

* 将帮助命令中输出的`Config File Example`写入到一个配置文件中，命名为`config.properties`
* 根据自己的环境信息配置好配置文件
* 运行命令`hcfup -c config.properties`即可
* 配置文件可以有多个，通过-c指定不同的配置文件就行了，比如`hcfup -c config1.properties`或者`hcfup -c config2.properties`