# EgernRules

[![Build](https://github.com/Repcz/EgernRules/actions/workflows/Build.yml/badge.svg)](https://github.com/Repcz/EgernRules/actions/workflows/Build.yml)
![License](https://img.shields.io/badge/license-MIT-blue)

> 基于 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) 自动转换的 [Egern](https://egernapp.com/) 规则集，每日 UTC 0:30 自动更新。

---

## 特点

- **全自动构建** — GitHub Actions 每天自动同步上游数据并转换格式
- **Egern 原生 YAML 格式** — 严格遵循 [官方规则文档](https://doc.egernapp.com/zh-CN/docs/configuration/rules) 规范
- **完整类型覆盖** — 支持 `domain_set` / `domain_suffix_set` / `domain_keyword_set` / `domain_wildcard_set` / `ip_cidr_set` / `ip_cidr6_set` / `asn_set` / `url_regex_set` / `user_agent_set` / `dest_port_set` / `geoip_set`
- **排序去重** — 规则按类型分组、字母序排列、大小写不敏感去重
- **即拿即用** — 可直接用于 Egern 的 `rule_set` 引用（支持 `update_interval` 自动更新）

## 使用方式

在 Egern 主配置的 `rules` 段中通过 `rule_set` 类型引用远程规则集文件：

```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/Repcz/EgernRules/X/Rules/<规则名称>/<规则名称>.yaml"
      policy: <策略名>
      update_interval: 86400
```

### 示例

```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/Repcz/EgernRules/X/Rules/Google/Google.yaml"
      policy: Proxy
      update_interval: 86400
  - rule_set:
      match: "https://raw.githubusercontent.com/Repcz/EgernRules/X/Rules/Apple/Apple.yaml"
      policy: DIRECT
      update_interval: 86400
  - rule_set:
      match: "https://raw.githubusercontent.com/Repcz/EgernRules/X/Rules/Reject/Reject.yaml"
      policy: REJECT
      update_interval: 86400
```

## 规则列表

[点此查看所有可用规则](https://github.com/Repcz/EgernRules/tree/X/Rules)

## 转换说明

本项目自动将 Surge 格式的 `.list` 规则转换为 Egern 兼容的 `.yaml` 格式：

### 规则类型映射

| Surge 格式 | Egern YAML 键 | 值格式 |
|-----------|--------------|--------|
| `DOMAIN,` | `domain_set:` | 纯文本 |
| `DOMAIN-SUFFIX,` | `domain_suffix_set:` | 纯文本 |
| `DOMAIN-KEYWORD,` | `domain_keyword_set:` | 纯文本 |
| `DOMAIN-WILDCARD,` | `domain_wildcard_set:` | 纯文本 |
| `IP-CIDR,` | `ip_cidr_set:` | 纯文本 |
| `IP-CIDR6,` | `ip_cidr6_set:` | 纯文本 |
| `GEOIP,` | `geoip_set:` | 纯文本 |
| `IP-ASN,` | `asn_set:` | 引号包裹 `- "AS15169"` |
| `URL-REGEX,` | `url_regex_set:` | 引号包裹 `- "^https://"` |
| `USER-AGENT,` | `user_agent_set:` | 引号包裹 `- "*Chrome*"` |
| `DEST-PORT,` | `dest_port_set:` | 引号包裹 `- "80,443"` |

> 引用值包含 YAML 特殊字符（`*`、`^`、`,` 等）的类型，自动添加引号确保解析正确。

### 不支持的规则类型

以下类型在转换时自动剔除：

| 类型 | 原因 |
|------|------|
| `PROCESS-NAME` | Egern 不支持进程名匹配 |
| `AND` / `OR` / `NOT` | 规则集内不支持逻辑组合 |

### 输出示例

```yaml
# 规则名称: Google
# 规则统计: 128

domain_set:
  - google.com

domain_suffix_set:
  - google.com
  - googleapis.com

ip_cidr_set:
  - 8.8.8.0/24

asn_set:
  - "AS15169"

url_regex_set:
  - "^https://www\\.google\\.com/"
```

## 数据来源

- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) — 上游 Surge 规则数据

## 许可证

[MIT](LICENSE)
