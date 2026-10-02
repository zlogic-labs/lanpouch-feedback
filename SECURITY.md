# Security Policy

## 请不要开公开 issue

**support@zlogic.run**

公开 issue 在补丁发布之前，等于把可利用的细节交给所有人。请发邮件。

请在邮件里写清：

- 两端的 LanPouch 版本
- 复现步骤
- 受影响的系统与设备
- 你观察到的现象（不需要写怎么利用）

我会确认收到，然后在公开 issue 里同步一条**不含利用细节**的说明，修好之后发布版本。

## 这个产品已经知道的边界

不是漏洞，是设计取舍，写在这里免得被当成漏洞报一遍：

- **局域网内传输不加密。** 桌面端走 HTTP 而非 HTTPS，文件内容和访问令牌在网线上是明文。
  同一 WiFi 下能抓包的人可以读到。详见[隐私政策](https://lanpouch.zlogic.run/privacy/)。
- **桌面端监听所有网络接口**，任何能访问到该机器本地地址的设备都可以尝试连接。
  未配对会被拒绝，但端口是可达的。
- **iOS 切后台会断连。** 这是 iOS 不允许应用维持裸 TCP 连接导致的，不是缺陷。

## 如果你只是想报个 bug

普通缺陷请直接用 [Bug report 模板](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=bug_report.yml)。