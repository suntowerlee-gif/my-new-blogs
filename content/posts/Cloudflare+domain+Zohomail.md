+++
date = '2025-12-03T22:17:33+08:00'
draft = false
title = 'Cloudflare+domain+Zohomail'

+++

**Cloudflare 的解析速度极快且生效迅速，配合 Zoho Mail 的免费版（永久免费计划），是目前搭建稳定企业/个人域名邮箱的最佳零成本方案之一。**

请注意：Zoho Mail 的永久免费版（Forever Free Plan）包含 **5 个用户**，每个用户 **5GB 空间**，但**不支持 POP/IMAP**（即无法使用 Outlook、Apple Mail 等第三方桌面客户端，只能使用 Zoho 的网页版或官方手机 App）。按照以下详细步骤操作：

------

### 第一步：注册 Zoho Mail 免费版

Zoho 经常隐藏免费版的入口，请仔细按照以下路径寻找：

1. 访问 [Zoho Mail 定价页面](https://www.zoho.com/mail/zohomail-pricing.html)。
2. 向下滚动到页面底部，找到 **"Forever Free Plan"** (永久免费计划) 区域。
3. 点击 **"Sign Up Now"** (立即注册)。
4. 输入您的域名、手机号码（必须验证）、管理员账号名称（如 `admin` 或 `contact`）和密码。
5. 完成注册并登录到 Zoho Mail 的设置向导页面。

------

### 第二步：在 Cloudflare 中验证域名所有权

Zoho 需要确认这个域名是您的。它会提供一个 `TXT` 记录值（以 `zoho-verification` 开头）。

1. **在 Zoho 页面：** 复制显示的 **TXT 值**（Destination/Points to）。
2. **在 Cloudflare 页面：**
   - 登录 Cloudflare，点击您的域名。
   - 在左侧菜单选择 **DNS** > **Records** (记录)。
   - 点击 **Add record** (添加记录)。
   - **Type (类型):** 选择 `TXT`。
   - **Name (名称):** 输入 `@`（代表根域名）。
   - **Content (内容):** 粘贴刚刚从 Zoho 复制的一长串代码。
   - 点击 **Save** (保存)。
3. **回到 Zoho 页面：** 等待约 1 分钟，点击底部的 **"Verify by TXT"** (通过 TXT 验证)。
   - *提示：Cloudflare 生效很快，通常几秒钟即可验证成功。*

------

### 第三步：配置 MX 记录 (最关键一步)

这一步决定了别人发的邮件能准确投递到 Zoho 的服务器。

1. **在 Cloudflare 页面：**

   - **重要：** 如果您之前有其他的 MX 记录（例如来自 Godaddy 或主机商的），请先**删除**它们，以免冲突。
   - 点击 **Add record**。
   - **Type:** `MX`
   - **Name:** `@`
   - **Mail server:** `mx.zoho.com`
   - **Priority:** `10`
   - 点击 **Save**。

   *重复上述步骤，添加第二条和第三条（作为备用）：*

   - Type: `MX`, Name: `@`, Server: `mx2.zoho.com`, Priority: `20`
   - Type: `MX`, Name: `@`, Server: `mx3.zoho.com`, Priority: `50`

2. **回到 Zoho 页面：** 点击 **MX Lookup** 或 **Verify** 按钮确认。

------

### 第四步：配置 SPF 和 DKIM (防止被当做垃圾邮件)

为了让您发出的邮件不进入别人的垃圾箱，这两步必须做。

#### 1. 配置 SPF

- **在 Zoho 页面：** 找到 SPF 配置部分，复制类似 `v=spf1 include:zoho.com ~all` 的值。
- **在 Cloudflare 页面：**
  - Add record > Type: `TXT` > Name: `@` > Content: `v=spf1 include:zoho.com ~all`。
  - 点击 **Save**。

#### 2. 配置 DKIM (强烈建议)

- **在 Zoho 页面：** 进入管理控制台，找到 **DKIM** 设置。
  - 选择您的域名，点击 **Configure** (配置)。
  - 它会生成一个 **Selector** (通常您可以自定义，比如输入 `zmail`) 和一个长 **TXT 值**。
- **在 Cloudflare 页面：**
  - Add record > Type: `TXT`。
  - **Name:** 输入 Zoho 提供的 Selector 名称，例如 `zmail._domainkey` (注意不要漏掉 `._domainkey` 部分)。
  - **Content:** 粘贴 Zoho 生成的那一长串公钥代码。
  - 点击 **Save**。
- **回到 Zoho 页面：** 点击 **Verify** 验证 DKIM 签名。

------

### 第五步：完成设置与测试

1. **创建用户：** 在 Zoho 向导中，您可以跳过“邮件迁移”和“移动端下载”步骤，直接进入收件箱。
2. **测试接收：** 用您的个人 Gmail 给新邮箱发一封信。
3. **测试发送：** 用新邮箱回复一封信，并检查 Gmail 是否收到，以及是否进入了垃圾箱（如果 SPF/DKIM 设置正确，应该直接进入收件箱）。
