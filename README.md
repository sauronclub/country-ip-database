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


### 方式二：本地运行更新
# 克隆仓库
git clone https://github.com/sauronclub/country-ip-database.git
cd country-ip-database

# 安装依赖
pip install -r requirements.txt

# 更新IP数据
python scripts/update_ranges.py
📁 数据格式
country-ip-database/
├── data/
│   ├── ipv4/
│   │   ├── CN.json      # 中国
│   │   ├── US.json      # 美国
│   │   ├── JP.json      # 日本
│   │   └── ...          # 其他国家
│   └── ipv6/
│       ├── CN.json
│       └── ...
└── scripts/
    ├── update_ranges.py
    └── upload_to_r2.py
JSON文件格式：

[
  "1.0.0.0/24",
  "1.1.1.0/24",
  "1.2.3.0/24",
  ...
]
🔄 更新策略
更新频率：每日自动更新
智能更新：仅当该国家IP段发生变化时才更新文件
无变化不更新：如果某国家IP段与上次一致，对应文件保持不变
📊 数据统计
类型	数量
支持国家/地区	239
IPv4文件	239
IPv6文件	239
更新周期	每日
🛠️ 使用示例
Python 示例
import json

# 读取中国IP段
with open('data/ipv4/CN.json', 'r') as f:
    cn_ips = json.load(f)

print(f"中国共有 {len(cn_ips)} 个IP段")
print(f"前5个IP段: {cn_ips[:5]}")
Node.js 示例
const fs = require('fs');

// 读取中国IP段
const cnIps = JSON.parse(
  fs.readFileSync('data/ipv4/CN.json', 'utf8')
);

console.log(`中国共有 ${cnIps.length} 个IP段`);
🔧 技术栈
Python 3.8+ - 数据处理
GitHub Actions - 自动化更新
Cloudflare R2 - 数据存储（可选）
📝 支持的国家代码
所有支持的国家/地区代码：

AD, AE, AF, AG, AI, AL, AM, AO, AQ, AR, AS, AT, AU, AW, AX, AZ, ...

查看完整列表 →

🤝 贡献
欢迎以下形式的贡献：

报告数据问题
改进数据处理脚本
完善文档
📄 许可
MIT License - 详见 LICENSE 文件

📧 联系
GitHub: @sauronclub
Issues: 提交问题
