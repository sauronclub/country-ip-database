全球IP段API / Global IP Ranges API
<div align="center">
https://opensource.org/licenses/MIT
https://github.com/sauronclub/global-ip-ranges/actions
https://www.cloudflare.com/
免费 · 自动更新 · CDN加速 / Free · Auto-updated · CDN Accelerated
</div>
🌟 项目简介 / Project Overview
这是一个完全免费的开源项目，提供全球各国IPv4和IPv6地址段数据。数据直接来源于五大区域互联网注册机构（RIR），每周自动更新，并通过Cloudflare全球CDN加速，响应时间<50ms。
This is a completely free and open-source project providing global IPv4 and IPv6 address ranges by country. Data is sourced directly from five Regional Internet Registries (RIRs), automatically updated weekly, and accelerated via Cloudflare's global CDN with <50ms response time.
🎯 核心特性 / Key Features
100% 免费 / 100% Free: 完全使用GitHub Actions + Cloudflare R2 + CDN免费额度
每周自动更新 / Weekly Auto-update: GitHub Actions每周一凌晨自动运行
官方权威数据 / Official Data: 直接源自APNIC、ARIN、RIPE、LACNIC、AFRINIC
全球CDN加速 / Global CDN: Cloudflare边缘缓存，全球50ms内响应
零运维 / Zero Maintenance: 配置完成后无需任何人工干预
📁 数据格式 / Data Format
目录结构 / Directory Structure
复制
data/
├── ipv4/
│   ├── CN.json          # 中国IPv4地址段 / China IPv4 ranges
│   ├── US.json          # 美国IPv4地址段 / US IPv4 ranges
│   └── ...              # 共238个国家/地区 / 238 countries/regions
└── ipv6/
    ├── CN.json
    ├── US.json
    └── ...              # 共231个国家/地区 / 231 countries/regions
JSON格式示例 / JSON Format Example
JSON
复制
// https://api.yourdomain.com/ipv4/CN.json
[
  "1.0.1.0/24",
  "1.0.2.0/23",
  "1.0.8.0/21",
  "... 约8000个中国IPv4段 / ~8000 Chinese IPv4 CIDRs"
]
🔥 快速开始 / Quick Start
HTTP直接访问 / Direct HTTP Access
bash
复制
# 获取中国所有IPv4地址段
# Fetch all IPv4 ranges for China
curl https://api.yourdomain.com/ipv4/CN.json

# 获取日本所有IPv6地址段
# Fetch all IPv6 ranges for Japan
curl https://api.yourdomain.com/ipv6/JP.json
Python集成 / Python Integration
Python
复制
import requests

def get_country_ip_ranges(country_code: str, ip_version: str = 'ipv4'):
    """
    获取指定国家的IP地址段
    Get IP ranges for a specific country
    """
    url = f"https://api.yourdomain.com/{ip_version}/{country_code.upper()}.json"
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    return response.json()

# 使用示例 / Usage Example
if __name__ == "__main__":
    cn_ranges = get_country_ip_ranges('CN', 'ipv4')
    print(f"中国共有 {len(cn_ranges)} 个IPv4地址段")
    # Output: China has ~8000 IPv4 CIDR blocks
    
    jp_ipv6 = get_country_ip_ranges('JP', 'ipv6')
    print(f"日本共有 {len(jp_ipv6)} 个IPv6地址段")
    # Output: Japan has ~3000 IPv6 CIDR blocks
Node.js集成 / Node.js Integration
JavaScript
复制
async function getIPRanges(country, version = 'ipv4') {
    /**
     * 获取指定国家的IP地址段
     * Fetch IP ranges for a specific country
     */
    const url = `https://api.yourdomain.com/${version}/${country.toUpperCase()}.json`;
    const response = await fetch(url);
    if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response.json();
}

// 使用示例 / Usage Example
(async () => {
    const usIPs = await getIPRanges('US', 'ipv6');
    console.log(`美国共有 ${usIPs.length} 个IPv6地址段`);
    // Output: US has ~3000 IPv6 CIDR blocks
})();
🛠️ 技术架构 / Tech Architecture
核心组件 / Core Components
数据采集 / Data Collection: GitHub Actions (定时Cron任务)
数据存储 / Storage: Cloudflare R2 (兼容S3的对象存储)
内容分发 / Distribution: Cloudflare CDN (全球300+节点)
源数据 / Raw Data: 官方RIR FTP服务器
RIR数据源 / RIR Data Sources
表格
复制
区域 / Region	RIR	数据源URL
亚太 / Asia Pacific	APNIC	https://ftp.apnic.net/stats/apnic/
北美 / North America	ARIN	https://ftp.arin.net/pub/stats/arin/
欧洲 / Europe	RIPE NCC	https://ftp.ripe.net/pub/stats/ripencc/
拉美 / Latin America	LACNIC	https://ftp.lacnic.net/pub/stats/lacnic/
非洲 / Africa	AFRINIC	https://ftp.afrinic.net/pub/stats/afrinic/
📅 更新机制 / Update Mechanism
自动更新 / Automatic Updates
频率: 每周一 00:00 UTC
触发器: GitHub Actions定时任务
流程: 下载RIR数据 → 解析 → 生成JSON → 推送到GitHub仓库和R2
手动触发 / Manual Trigger
进入GitHub仓库 → Actions → Update IP Ranges → Run workflow
💰 成本分析 / Cost Analysis
永久免费 (在免费额度范围内)
表格
复制
服务 / Service	免费额度 / Free Quota	实际用量 / Actual Usage	月费用 / Monthly Cost
GitHub Actions	2000分钟/月	~8分钟/月	¥0 / $0
Cloudflare R2存储	10GB	~50MB	¥0 / $0
Cloudflare R2操作	100万次B类操作	~800次写入/月	¥0 / $0
Cloudflare CDN流量	无限流量	缓存读取	¥0 / $0
总计 / Total	-	-	¥0 / $0
🚀 部署你自己的实例 / Deploy Your Own
前置条件 / Prerequisites
✅ GitHub账号
✅ Cloudflare账号
✅ 已接入Cloudflare的域名
部署步骤 / Deployment Steps
Fork本仓库 / Fork this repository
创建R2存储桶 / Create R2 Bucket
登录Cloudflare Dashboard → R2 Storage
创建存储桶：ip-ranges
开启 Public Access
绑定自定义域名：api.yourdomain.com
配置GitHub Secrets / Configure GitHub Secrets
在仓库 Settings → Secrets → Actions 中添加：
bash
复制
R2_ACCOUNT_ID=你的R2账号ID
R2_ACCESS_KEY_ID=你的访问密钥ID
R2_SECRET_ACCESS_KEY=你的密钥
R2_BUCKET=ip-ranges
触发首次运行 / Trigger First Run
进入 Actions → Update IP Ranges
点击 Run workflow
验证部署 / Verify Deployment
bash
复制
curl https://api.yourdomain.com/ipv4/CN.json
📊 项目状态 / Project Status
✅ 数据完整性: 238个IPv4国家文件，231个IPv6国家文件
✅ 自动化: 每周自动更新已验证
✅ CDN加速: 全球边缘缓存已启用
✅ 成本: 完全在免费额度内
📜 许可证 / License
数据许可 / Data License: 所有数据来源于官方RIR，属于公有领域。
代码许可 / Code License: MIT License
🤝 贡献 / Contributing
欢迎提交Issue或Pull Request！
可贡献的方向:
数据验证和清洗
性能优化
文档改进
新增功能提议
💬 支持 / Support
如果这个项目对你有帮助，请给一颗 ⭐ Star！
联系方式:
提交Issue: Issues页面
技术讨论: Discussions页面
<div align="center">
用心为开发者打造，由开发者创造。
Built with ❤️ for developers, by developers.
</div>
