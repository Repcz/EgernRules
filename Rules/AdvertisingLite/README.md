# 🧸 去广告精简版

## 前言

![](https://shields.io/badge/-移除重复规则-ff69b4) ![](https://shields.io/badge/-移除无法解析的域名-important) ![](https://shields.io/badge/-DOMAIN与DOMAIN--SUFFIX合并-green) ![](https://shields.io/badge/-DOMAIN--SUFFIX间合并-critical) ![](https://shields.io/badge/-DOMAIN与DOMAIN--KEYWORD合并-9cf) ![](https://shields.io/badge/-DOMAIN--SUFFIX与DOMAIN--KEYWORD合并-blue) ![](https://shields.io/badge/-IP--CIDR(6)合并-blueviolet) ![](https://shields.io/badge/-MITM--DOMAINNAME合并-brightgreen) ![](https://shields.io/badge/-正则推导DOMAINNAME-033da7) 

去广告精简版规则由《RULE GENERATOR 规则生成器》自动生成。

分流规则是互联网公共服务的域名和IP地址汇总，所有数据均收集自互联网公开信息，不代表我们支持或使用这些服务。

请通过【中华人民共和国 People's Republic of China】合法的互联网出入口信道访问规则中的地址，并确保在使用过程中符合相关法律法规。

## 规则说明
可能存在部分误拦截，建议搭配放行规则进行修正。

## 规则统计

最后更新时间：2024-12-16 02:08:39

各类型规则统计：
| 类型 | 数量(条)  | 
| ---- | ----  |
| AND | 1  | 
| DOMAIN | 23745  | 
| DOMAIN-KEYWORD | 187  | 
| DOMAIN-SUFFIX | 13910  | 
| IP-CIDR | 184  | 
| IP-CIDR6 | 1  | 
| URL-REGEX | 2  | 
| TOTAL(仅供参考) | 38030  | 


## Surge 

#### 使用说明
- AdvertisingLite.yaml，请使用RULE-SET。
- AdvertisingLite_Resolve.yaml，请使用RULE-SET。
- AdvertisingLite_Domain.yaml，请使用DOMAIN-SET。
- URL-REGEX类型的规则，在HTTPS协议中，需要配合MITM使用。规则生成器已尝试推导MITM的配置AdvertisingLite_MITM.sgmodule，仅供参考。

#### 文件区别
- AdvertisingLite_All.yaml与AdvertisingLite_All_No_Resolve.list为 Surge 5.21.0(2952) 以上版本使用
- AdvertisingLite_Resolve.yaml与AdvertisingLite.list的区别仅在于后者IP-CIDR(6)类型带no-resolve。

#### 配置建议
- Surge 5.21.0(2952)以上版本使用以下配置：
- AdvertisingLite_All.yaml 单独使用。
- AdvertisingLite_All_No_Resolve.yaml 单独使用。
- Surge 5.21.0(2952)以下版本使用以下配置：
- AdvertisingLite.yaml、AdvertisingLite_Domain.list 共同使用。
- AdvertisingLite_Resolve.yaml、AdvertisingLite_Domain.list 共同使用。

#### 规则链接
**X分支 (每日更新)**

https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/AdvertisingLite/AdvertisingLite.list






https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/release/rule/Surge/AdvertisingLite/AdvertisingLite.list





## 子规则/排除规则


当前分流规则，未包含其他子规则。

当前分流规则，已排除以下规则：
| 排除规则  |  | 
| ---- | ----  |
| Hijacking | Privacy  | 

## 数据来源

《去广告精简版》的数据来自以下链接，如与本项目的《去广告精简版》规则混合使用，可能会造成规则大量重复。

- https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanAD.list
- https://raw.githubusercontent.com/NobyDa/ND-AD/master/Surge/AD_Block.txt
- https://raw.githubusercontent.com/NobyDa/Script/master/Surge/AdRule.list
- https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/source/rule/Advertising/Advertising.list
- https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/source/rule/Advertising/LianXiangJia/LianXiangJia.list
- https://raw.githubusercontent.com/yjqiang/surge_scripts/main/modules/hupu/hupu.sgmodule
- https://raw.githubusercontent.com/fmz200/wool_scripts/main/QuantumultX/filter/fenliu.list


感谢以上规则作者的辛勤付出（排名不分先后）。

## 最后

### 感谢

[@fiiir](https://github.com/fiiir) [@Tartarus2014](https://github.com/Tartarus2014) [@zjcfynn](https://github.com/zjcfynn) [@chenyiping1995](https://github.com/chenyiping1995) [@vhdj](https://github.com/vhdj)

提供规则数据源及改进建议。

### 其他

请不要对外宣传本项目。