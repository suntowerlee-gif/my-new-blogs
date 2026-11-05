+++
title = "PDF 受控副本工具（PDF Controlled Copy）"
description = "把 PDF 转成带有效期控制的受控电子副本：过期后自动提示并隐藏正文，可加水印、AES-256 密码。当前版本 v1.2，中英文两个版本。"
date = '2026-11-05T09:20:00+08:00'
summary = "把任意 PDF 生成为带有效期的受控电子副本：有效期内正常阅读，过期后弹窗警告并隐藏正文；支持水印、页脚标识、AES-256 加密和批量处理。当前版本 v1.2。"
weight = 5
tags = ["Windows", "PDF", "文件控制", "小工具"]
+++

{{< lead >}}
SOP、方法、标准等电子文件被下载、转发后，常常在新版本生效后仍被继续使用。**PDF 受控副本工具**为 PDF 生成带有效期的「受控电子副本」，原理与企业文件管理系统发布的受控 PDF 相同。
{{< /lead >}}

{{< button href="/downloads/PDFControlledCopy-v1.2-CN.exe" >}}下载 v1.2（中文版，.exe）{{< /button >}}&nbsp;&nbsp;
{{< button href="/downloads/PDFControlledCopy-v1.2-EN.exe" >}}Download v1.2 (English){{< /button >}}&nbsp;&nbsp;
{{< button href="https://suntower.gumroad.com/l/keewo" target="_blank" rel="noopener" >}}Gumroad 购买{{< /button >}}

## 不同阅读器中的效果

| 打开方式 | 看到的内容 |
|---|---|
| Adobe Acrobat / Reader（启用 JavaScript），有效期内 | 正文 + 水印 + 页脚有效期标识 |
| Adobe Acrobat / Reader，已过期 | 弹窗警告，正文隐藏，每页显示过期提示 |
| 浏览器、WPS、关闭 JavaScript 的 Acrobat | 只显示「需要 JavaScript」提示页 |

## 功能

- **有效期**：有效时长（小时 / 天）或指定截止时间；可选生效时间
- **过期处理**：弹窗警告、隐藏正文、每页显示过期提示（均可开关）
- **页脚 / 页眉有效期标识**：任何阅读器和打印件上都可见
- **水印**：文字、字号、角度、不透明度、颜色，平铺或居中
- **AES-256 加密**：打开密码、权限密码（打印 / 复制 / 编辑）
- **批量处理**：添加文件或整个文件夹（含子文件夹）；混合页面尺寸、旋转页面均可正确处理
- 所有提示文字可修改；设置自动保存（密码除外）

## 运行环境

- 制作受控副本：Windows 10 / 11，单个 exe，无需安装
- 阅读受控副本：Adobe Acrobat 或免费的 Adobe Acrobat Reader，启用 JavaScript（默认启用）
- 首次运行从网上下载的 exe 时，Windows 可能提示“已保护你的电脑”，点「更多信息 → 仍要运行」即可

## 软件授权

软件需授权后使用，每台电脑只需激活一次：

1. 首次打开时显示本机 16 位机器码，点「复制」
2. 在 Gumroad 购买后，按收据中的说明提供机器码，获得授权码
3. 把授权码粘贴到「授权码」框，点「激活」

中文版与英文版共用授权码；授权码只对申请时的那台电脑有效，重装系统或更换系统盘后需要重新获取。本软件仅限个人使用。

## 使用前请注意

本工具用于文件管控和防误用，**不是 DRM**，应配合文件管理程序使用：

- 有效期以打开者电脑的系统时间为准
- 正文仍保存在文件中，专业 PDF 工具可以提取
- 仅设置权限密码时可被专业工具去除；设置打开密码才是真正加密

## 更新记录

- **v1.2**：当前版本，中文版 + English 版

## 其它软件

[Word 批量转 PDF（Windows 版）]({{< ref "software/word-to-pdf-windows" >}}) · [Word 批量转 PDF（Android 版）]({{< ref "software/word-to-pdf-android" >}})

---

版权所有 © 2026 Suntower Lee。
