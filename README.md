# LanPouch — 反馈

**[English](#english) · 中文**

LanPouch 是局域网内的手机/平板 ↔ 电脑文件同步工具。**源码闭源**，本仓库不包含代码，只收反馈。

- 产品主页：<https://lanpouch.zlogic.run>
- 隐私政策：<https://lanpouch.zlogic.run/privacy/>
- 联系方式：support@zlogic.run

## 该在这里提什么

| 类型 | 用哪个模板 |
|---|---|
| 功能坏了、结果不对、传丢了文件 | [Bug report](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=bug_report.yml) |
| 想要某个能力，或者现有行为不合理 | [Feature request](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=feature_request.yml) |
| 上面都不合适 | 直接开 issue |

## 不该在这里提的

**安全问题请发邮件到 support@zlogic.run，不要开公开 issue。**
在补丁发布之前，公开 issue 等于把可利用的细节交给所有人。邮件里请写清版本和复现步骤，
我会先确认收到再在公开 issue 里同步一条不含利用细节的说明。

**许可证问题。** 本项目闭源发布，不授予任何开源许可证。看到"LanPouch"这个仓库不代表可以
拿去改用或再分发。

## 报 bug 前请先看

大部分"连不上"不是 bug，是网络环境挡住了。这两类占了已知限制里的大头：

- **必须同一网段。** 手机连的是访客网络、4G/5G 蜂窝数据、和电脑不同子网，都不行。
  mDNS 组播不会跨子网。
- **AP 隔离。** 企业/校园/酒店 WiFi 默认开启，组播和单播都会被阻断，表现就是扫码搜不到电脑。
- **电脑端要在运行。** 它是常驻监听，不是被唤醒的服务。
- **iOS 切后台会断。** iOS 不允许应用在后台维持裸 TCP 连接，切出去正在传的会中断。
  续传队列在本地，重新打开会自己继续，但"关掉 App 也能同步"做不到。
- **防火墙。** Windows 首次启动会弹窗，选了"取消"或"阻止"就只能手动放行了。

## 请务必附上

不说清楚这几项，基本没法复现：

1. LanPouch 版本（两端都要）
2. 电脑系统与版本、手机型号与系统版本
3. **网络拓扑**——电脑接的是网线还是 WiFi？手机连的是哪个 SSID？两者同一个路由器吗？
   路由器开了访客网络或 AP 隔离吗？
4. 完整日志。桌面端日志在应用数据目录下的 `lanpouch.log`；手机端在应用内「日志」页。

第 3 条是关键。同一个现象在"同一网段"和"开了访客网络"两种情况下，原因完全不同，
没有网络信息的话我只能靠猜。

## 关于响应

这是一个小项目，没有值班，也没有 SLA。我会尽力回，但不是每次都能当天回。
回复语言跟随你提问的语言。

如果你愿意提 PR：这个仓库没有源代码，拉取请求帮不上忙——但如果你在 issue 里附上复现
步骤、补丁或想法，那对定位问题很有帮助。

---

<a name="english"></a>

# LanPouch — Feedback

LanPouch syncs files between your phone/tablet and your computer over your local
network. **The source is closed.** This repository contains no code; it is for
feedback only.

- Home: <https://lanpouch.zlogic.run>
- Privacy policy: <https://lanpouch.zlogic.run/privacy/>
- Contact: support@zlogic.run

## What belongs here

| Type | Template |
|---|---|
| Something broke, produced a wrong result, or lost a file | [Bug report](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=bug_report.yml) |
| You want a capability, or existing behaviour is wrong | [Feature request](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=feature_request.yml) |
| Neither fits | Open an issue |

## What does not

**Please email security issues to support@zlogic.run rather than opening a public
issue.** A public issue hands usable detail to everyone before a fix ships. Include
the version and reproduction steps; I will confirm receipt and follow up with a
public issue that contains no exploit detail.

**Licensing.** LanPouch ships closed source and carries no open-source licence.
Seeing the LanPouch name does not grant rights to modify or redistribute it.

## Check these before filing a bug

Most "it won't connect" reports are the network, not a bug:

- **Same subnet.** A guest network, cellular data, or a different subnet will not
  work. mDNS multicast does not cross subnets.
- **AP isolation.** Corporate, campus and hotel WiFi enable it by default; it
  blocks both multicast and unicast, which looks exactly like "the desktop never
  shows up in the scanner."
- **The desktop app must be running.** It listens while open; it is not a
  wake-on-demand service.
- **iOS backgrounds disconnect.** iOS does not allow bare TCP connections to
  persist in the background, so backgrounding the app interrupts an active
  transfer. The resume queue is local and picks up on reopen, but "syncs while
  closed" is not possible.
- **Firewall.** Windows prompts on first launch; choosing Cancel or Block leaves
  the app unreachable until you allow it manually.

## Always include

Without these, reproduction is guesswork:

1. LanPouch version on **both** ends
2. Computer OS and version, phone model and OS version
3. **Network topology** — is the computer on ethernet or WiFi? Which SSID is the
   phone on? Same router? Guest network or AP isolation enabled?
4. Full logs. On desktop, `lanpouch.log` in the application data directory; on
   mobile, the Log screen in the app.

Item 3 is the one that matters. The same symptom has completely different causes
with and without a guest network, so without it I can only guess.

## On response times

This is a small project with no on-call rotation and no SLA. I will reply where I
can, but not always the same day. I answer in the language you asked in.

Pull requests: this repository has no source code, so a pull request will not help.
But reproduction steps, a patch, or an idea inside an issue genuinely does.