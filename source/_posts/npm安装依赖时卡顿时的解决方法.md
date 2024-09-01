---
title: npm安装依赖时卡顿时的解决方法
date: 2024-09-01 19:59:34
tags: [npm, Node.js]
---

npm install安装依赖时卡顿时的解决方法：

#### 1. 检查网络状况

首要任务是确保您的计算机具有稳定的网络连接，并能无障碍访问外部资源。如果是在公司或校园内网环境下，检查是否存在防火墙限制或代理服务器对NPM仓库访问的影响。

#### 2. 切换至国内镜像源（√）

由于地理原因，直接访问NPM官方仓库（registry.npmjs.org）可能速度较慢甚至不稳定。这时，切换至国内高速[NPM镜像](https://so.csdn.net/so/search?q=NPM镜像&spm=1001.2101.3001.7020)源是一个不错的选择。例如使用淘宝NPM镜像：

```bash
npm config set registry https://registry.npmmirror.com
```

设置完成后，重新执行 `npm install` 尝试安装依赖。

#### 3. 显示详细日志以定位问题

通过增加命令的详细日志输出级别，可以更好地了解安装过程中哪个环节出现问题：

```bash
npm install --verbose
```

详尽的日志信息有助于我们找到导致卡顿的具体包及其原因。

#### 4. 清理缓存并重新尝试安装

本地npm缓存的问题也可能导致安装过程停滞不前。可以先清理缓存再重试安装：

```bash
npm cache clean --force
npm install
```

#### 5. 设置HTTP(S)代理（常见问题）

若你在受控网络环境中工作，需通过代理服务器访问互联网，请配置npm的代理设置：

```bash
npm config set proxy http://proxy.example.com:8080
npm config set https-proxy http://proxy.example.com:8080
```

请将示例中的代理地址替换为实际的代理服务器地址及端口。

#### 6. 分别安装特定大包

若怀疑某个大体积包在下载时引发问题，可尝试单独安装该包：

```bash
npm install <package-name>
```

#### 7. 更新NPM版本

升级到最新版npm也是解决此类问题的一个有效途径，因为新版npm可能会优化网络请求和依赖处理机制：

```bash
npm install -g npm
```

