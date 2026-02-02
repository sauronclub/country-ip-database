# Global Country IP Database

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Countries](https://img.shields.io/badge/Countries-239-green.svg)

## 📖 项目简介

全球 **239个国家/地区** 的IP地址段（CIDR）数据库，按国家分组整理的IPv4/IPv6地址库。

> 💡 **无需部署**：可直接下载 `data/` 目录下的JSON文件使用

## 🎯 核心价值

| 使用场景 | 说明 |
|---------|------|
| 地理IP定位 | 查询IP归属国家/地区 |
| 网络安全 | 区域IP封禁/白名单 |
| 访问控制 | 基于地域的访问策略 |
| 数据分析 | 区域流量统计 |

## 🌐 数据来源

数据源自五大区域互联网注册机构（RIR）：

- **APNIC** - 亚太地区
- **ARIN** - 北美地区
- **RIPE** - 欧洲地区
- **LACNIC** - 拉丁美洲
- **AFRINIC** - 非洲地区

## 🚀 快速开始

### 方式一：直接下载使用（推荐）

```bash
# 克隆仓库
git clone https://github.com/sauronclub/country-ip-database.git
cd country-ip-database/data/

# 获取中国IP段
cat ipv4/CN.json
