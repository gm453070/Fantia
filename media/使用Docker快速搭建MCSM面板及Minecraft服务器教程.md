# 使用Docker快速搭建MCSM面板及Minecraft服务器教程

## 一、MCSM面板与Mohist简介

### 1.1 MCSM面板优势
MCSManager（简称MCSM）是一款轻量级、全中文的Minecraft服务端管理面板，具有以下特点：
- 支持Docker容器化部署
- 多实例管理能力
- 完善的权限控制系统
- 开箱即用的操作体验

### 1.2 Mohist服务端特点
Mohist作为高性能Minecraft服务端解决方案：
- 同时支持Forge模组和Bukkit插件
- 基于Paper核心优化性能
- 提供稳定的运行环境
- 适合模组服和插件服搭建

## 二、服务器准备指南

### 2.1 硬件配置建议
| 服务器类型 | 推荐配置 |
|------------|----------|
| 1.17+纯净服 | 4核8G |
| 大型模组服 | 8核16G |
| 1.16.5以下 | 2核4G |

👉 [【点击查看】2025年最新雨云优惠码及特价云服务器方案汇总](https://bit.ly/RainYun)

## 三、详细搭建步骤

### 3.1 环境准备
1. 连接服务器（SSH工具推荐Xshell或MobaXterm）
2. 执行系统更新：
bash
apt update && apt upgrade -y

### 3.2 端口映射配置
必需映射的端口：
- 23333（面板访问）
- 24444（节点通信）
- 25565（游戏连接）

### 3.3 MCSM面板安装
执行一键安装脚本：
bash
wget -qO- https://gitee.com/mcsmanager/script/raw/master/setup.sh | bash

启动服务：
bash
systemctl start mcsm-{daemon,web}

### 3.4 Docker环境配置
安装Docker引擎：
bash
apt install docker.io
systemctl enable --now docker

## 四、服务器实例创建

### 4.1 服务端准备
1. 从[Mohist官网](https://new.mohistmc.com)下载核心文件
2. 通过面板上传.jar格式服务端

### 4.2 实例参数设置
关键配置项：
- 进程启动方式：虚拟化容器
- 环境镜像：mcsm-openjdk:17
- 网络模式：host
- 端口绑定：映射后的25565端口

### 4.3 首次启动流程
1. 修改eula.txt同意条款
2. 保存配置后重启实例
3. 通过控制台监控运行状态

## 五、客户端连接方法
在游戏多人游戏中输入：

服务器IP:映射端口

例如：play.example.com:30123

> 提示：建议使用域名而非IP地址，方便后续维护迁移