# Global Country IP Database

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

## 项目概述

提供全球 **239个国家/地区** 的IP地址段（CIDR）数据整理，按国家分组的IPv4/IPv6地址库。

## 核心价值

一键获取各国IP地址段数据，适用于：
- 地理IP定位
- 网络安全分析
- 区域访问控制
- IP地址归属查询

## 数据来源

数据源自五大区域互联网注册机构（RIR）：
- **APNIC** - 亚太地区
- **ARIN** - 北美地区  
- **RIPE** - 欧洲地区
- **LACNIC** - 拉丁美洲
- **AFRINIC** - 非洲地区

## 快速使用

### 获取数据

```bash
# 克隆仓库
git clone https://github.com/sauronclub/country-ip-database.git
cd country-ip-database

# 更新数据
python scripts/update_ranges.py
