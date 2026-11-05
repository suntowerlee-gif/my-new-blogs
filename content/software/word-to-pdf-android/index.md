+++
title = "Word 批量转 PDF（Android 版）"
description = "在手机上离线批量把 .docx 转为 PDF：不需要安装 Word，文件不会上传。当前版本 v1.0，支持 Android 10 及以上。"
date = '2026-11-05T09:00:00+08:00'
summary = "在手机上离线批量把 .docx 转为 PDF：不需要安装 Word，文件不会上传到任何服务器。当前版本 v1.0，支持 Android 10 及以上。"
weight = 20
tags = ["Android", "Word", "PDF", "小工具"]
+++

{{< lead >}}
在手机上离线把 Word（.docx）批量转换为 PDF。不需要安装 Word，转换在手机本地完成，**文件不会上传到任何服务器**。
{{< /lead >}}

{{< button href="https://github.com/suntowerlee-gif/sunsoftware/raw/main/Word2PdfBatchAndroid/release/Word%E6%89%B9%E9%87%8F%E8%BD%ACPDF_Android_v1.0.apk" target="_blank" rel="noopener" >}}下载 v1.0（Android，APK 约 26 MB）{{< /button >}}&nbsp;&nbsp;
{{< button href="https://github.com/suntowerlee-gif/sunsoftware/tree/main/Word2PdfBatchAndroid" target="_blank" rel="noopener" >}}说明与源码（GitHub）{{< /button >}}

## 功能

- **批量导入**：多选文件、导入整个文件夹（可含子文件夹），或在微信、QQ、文件管理中「用其他应用打开」「分享」到本 App
- **PDF 选项**：标准 / 最小文件大小（压缩图片，适合微信发送）、页码范围、显示修订标记、按标题创建书签、文档属性
- **保存位置**：「下载/Word转PDF」文件夹、与源文件相同的文件夹（文件夹导入时）、任意指定文件夹（可保留子文件夹结构）
- **同名处理**：自动重命名 / 覆盖 / 跳过
- 转换完成后，点击文件即可打开 PDF，也可以一次分享全部结果

## 转换原理

手机上没有 Word，App 内置了离线排版引擎：先把 .docx 渲染成网页，补上分页、页码、行距和字体映射，再通过 Android 打印接口生成矢量 PDF，因此 PDF 里的文字可以选择、可以搜索。内置思源宋体、思源黑体，以及与 Times New Roman、Arial、Calibri、Cambria、Courier New 字宽一致的字体，让换行和分页尽量接近 Word。

## 使用前请注意

- 仅支持 `.docx`（Word 2007 及以后的格式）。旧版 `.doc` 请先在 WPS 或 Word 中另存为 `.docx`
- 普通文字、表格、图片、页眉页脚、页码、横向页面都能正常转换；文本框、艺术字、复杂域代码、公式、特殊字体等可能与电脑版 Word 另存为 PDF 的效果有差异。对版式要求严格的正式文件，建议用 [Windows 版]({{< ref "software/word-to-pdf-windows" >}}) 转换
- 受密码保护的文档无法转换，会标记为失败并跳过
- 转换过程中请保持 App 在前台，屏幕会保持常亮直到转换结束

## 安装与授权

1. 把 APK 文件传到手机上点击安装。如提示“禁止安装未知来源应用”，按提示在设置中允许本次安装即可（不同品牌手机的说法略有不同）
2. 首次打开时显示本机 16 位设备码，点「发送给作者」可直接通过微信、邮件等发出
3. 收到授权码后点「从剪贴板粘贴」，再点「激活」

每台手机只需激活一次，授权码与 Windows 版使用同一套机制。卸载重装后设备码不变，可用同一个授权码重新激活；手机恢复出厂设置后设备码会变化，需要重新获取授权码。授权申请与使用问题请发邮件到 [suntowerlee@gmail.com](mailto:suntowerlee@gmail.com)。

## 更新记录

- **v1.0**：首个版本

---

版权所有 © 2026 Suntower Lee。未经作者允许，不得用于商业用途。
