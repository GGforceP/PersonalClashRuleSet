# PersonalClashRuleSet

> 面向 Mihomo / OpenClash 的个人规则与策略组配置。主要用于维护个人分流逻辑，并兼容 Sub-Store 覆写与可直接使用的完整 Mihomo 配置。

## 📁 仓库结构

```text
PersonalClashRuleSet/
├── README.md
├── Yaml/
│   ├── rules.yaml
│   ├── rules_full.yaml
│   └── rules_smart.yaml
└── Rules/
    ├── Edge_Copilot.yaml
    ├── Microsoft_Designer.yaml
    └── Microsoft_Edge_NewTab.yaml
```

| 路径 | 用途 | 链接 |
| --- | --- | --- |
| `Yaml/rules.yaml` | 主要规则成品，适用于 Sub-Store 等场景进行订阅转换/覆写；重点维护策略组、规则提供者与分流规则。 | [RAW文件](https://raw.githubusercontent.com/GGforceP/PersonalClashRuleSet/main/Yaml/rules.yaml) |
| `Yaml/rules_full.yaml` | 完整 Mihomo 配置模板，在 `Yaml/rules.yaml` 的规则体系基础上补充全局配置、`proxy-providers`、DNS、Sniffer、GEO 等基础配置。 | [RAW文件](https://raw.githubusercontent.com/GGforceP/PersonalClashRuleSet/main/Yaml/rules_full.yaml) |
| `Yaml/rules_smart.yaml` | Smart 内核专用派生配置。以 `Yaml/rules.yaml` 为基础，将自动测速组 Smart 化并启用 LightGBM；分流规则默认与基础配置同步。 | [RAW文件](https://raw.githubusercontent.com/GGforceP/PersonalClashRuleSet/main/Yaml/rules_smart.yaml) |
| `Rules/` | 存放单独整理、独立维护的自定义规则文件。新增自定义规则原则上放在此目录。 | — |

## 🚀 使用方法

### 方式一：搭配 Sub-Store（推荐）

1. 在 Sub-Store 的「订阅」页面添加自己的订阅。
2. 在「文件」页面新增一个 Mihomo 配置文件。
3. 在「JavaScript/YAML 覆写」中新增「脚本操作」。
4. 选择「远程链接」，填入本仓库 `Yaml/rules.yaml` 的 Raw 地址。
5. 点击「即时预览」，确认可以正常拉取并生成配置。
6. 保存后，将生成文件的分享链接导入使用 Mihomo/Clash 内核的客户端。
7. 后续规则更新后，只需在客户端更新订阅即可。

Sub-Store 项目：[sub-store-org/Sub-Store](https://github.com/sub-store-org/Sub-Store)

**优点**

- 一次部署后维护成本低，仓库规则更新后客户端刷新订阅即可。
- 兼容范围广，适用于 OpenClash、FlClash、Clash Verge、Stash 等使用 Clash/Mihomo 内核或兼容配置的客户端。

**注意**

- 自建 Sub-Store 服务时，需要保证客户端能够访问该服务；涉及 WAN 访问时还需要相应的公网访问或转发方案。

### 方式二：客户端直接引用覆写

以 FlClash 为例：

1. 打开「工具」→「进阶配置」。
2. 进入「脚本」，点击右上角「添加」。
3. 在配置编辑页选择「外部获取」→「通过 URL」。
4. 填入对应 YAML 的 Raw 地址，下载并保存。
5. 启用该配置后开始使用。

**优点**

- 可随时在自定义配置与默认配置之间切换。
- 不依赖额外的 Sub-Store 服务。

**注意**

- 部分客户端不支持远程覆写或外部配置引用，兼容性取决于客户端实现。

## 🧩 自定义规则维护

- `Rules/` 用于保存个人单独整理的规则。
- 新增规则前需要先检查是否已被现有 `rule-providers`、`GEOSITE`、`GEOIP` 或其他已引用规则覆盖，避免无意义重复。
- 如发现重复或包含关系，先说明重复来源与范围，再决定是否仍保留独立规则。
- 自行整理、仅参考其他项目部分信息形成的 `Rules/` 规则，默认不在 README 中增加致谢；仅在完整引用外部规则库或明确要求时标注来源。
- `Yaml/rules.yaml` 是默认的**基础分流源（Source of Truth）**。除非明确要求重新编写，所有其他规则 YAML 都以它为基础派生。
- 当 `Yaml/rules.yaml` 的策略组、规则提供者或 `rules` 发生基础修改时，应立即同步到 `Yaml/rules_full.yaml`、`Yaml/rules_smart.yaml` 及后续新增的其他派生规则 YAML；各文件只保留自身用途所需的专属差异。
- 仓库内部 `Rules/` 引用以及 README 中本仓库 Raw 链接必须与当前分支一致：`dev` 使用 `dev`，同步到 `main` 时相关 URL 必须一并切换到 `main`；外部仓库 URL 在可正常访问时保持不变。
- `Yaml/rules_smart.yaml` 仅维护 Smart 内核专属能力，例如 `type: smart`、LightGBM 等，不单独改变基础分流意图。

## 🌐 GEO 数据源

本仓库主要面向 OpenClash 使用，当前规则依赖的数据库来源如下：

| 类型 | 地址 |
| --- | --- |
| MMDB | [Country.mmdb](https://testingcf.jsdelivr.net/gh/alecthw/mmdb_china_ip_list@release/Country.mmdb) |
| GeoIP | [geoip.dat](https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geoip.dat) |
| GeoSite | [geosite.dat](https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geosite.dat) |
| ASN | [GeoLite2-ASN.mmdb](https://testingcf.jsdelivr.net/gh/xishang0128/geoip@release/GeoLite2-ASN.mmdb) |

需要自行扩展 GeoSite 分类时，可参考：[v2fly/domain-list-community](https://github.com/v2fly/domain-list-community)

## 🙏 鸣谢

- [Aethersailor/Custom_OpenClash_Rules](https://github.com/Aethersailor/Custom_OpenClash_Rules)
- [Sub-Store](https://github.com/sub-store-org/Sub-Store)

## 📝 更新日志

2026-10-6：  
增加了 `Yaml/rules_full.yaml`、`Yaml/rules_smart.yaml` 和 `Rules/Microsoft_Designer.yaml`，更新了 Microsoft Designer 分流规则和仓库内部规则引用分支。
