# vps-check
这是一个简洁高效的域名可视化展示面板，基于Cloudflare Workers构建。它提供了一个直观的界面，让用户能够一目了然地查看他们VPS的状态、注册商、注册日期、过期日期和使用进度，并可在到期前通过TG机器人向用户推送通知。

## 部署方法

### 1、workers部署
在cf中创建一个workers，复制`_worker.js`中的代码到workers中，点击保存并部署。

[![快速部署到 CF Worker](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/yutian81/vps-check)

### 2、pages部署
fork本仓库，在cf中创建一个pages，链接到你fork的仓库，点击部署

## 变量设置
| 变量名 | 填写示例 | 说明 | 是否必填 | 
| ------ | ------- | ------ | ------ |
| SITENAME | 我的域名监控 | 自定义站点名称，默认为`域名监控` | 否 |
| DOMAINS | `https://raw.githubusercontent.com/用户名/仓库名/main/domains.json` | 域名信息json文件 | 是 |
| TGID | 6522584277 | TG机器人ID | 否 |
| TGTOKEN | 6094768843:BBCrcWzLbXghYU8vdtt0jyESjpL9-uKM7p8 | TG机器人TOKEN | 否 |
| DAYS | 7 | 提前几天发送TG提醒，必须是整数 | 否 |

## 域名信息json文件格式
**示例**，请修改其中信息为你自己的vps
```
[
  { "country": "香港", "system": "Akile", "asn": "AS61112 Akile", "type": "VPS", "registrationDate": "2024-04-12", "expirationDate": "2025-04-12", "systemURL": "https://akile.io" },
  { "country": "巴西", "system": "DCI-FD5", "asn": "AS31898 Oracle", "type": "NAT", "registrationDate": "2024-08-19", "expirationDate": "2024-11-16", "systemURL": "https://dash.duckyci.com" },
  { "country": "波兰", "system": "Serv00-S9", "asn": "AS57367 Atman", "type": "容器", "registrationDate": "2024-08-18", "expirationDate": "2034-08-20", "systemURL": "https://panel9.serv00.com" }
]
```

## 相关截图
TG通知截图  
![TG提醒](https://fastly.jsdelivr.net/gh/yutian81/yutian81.github.io@master/assets/images/17243062899351724306289601.png)

监控页面截图  
![监控页面](https://fastly.jsdelivr.net/gh/yutian81/yutian81.github.io@master/assets/images/17243063439351724306343197.png)
