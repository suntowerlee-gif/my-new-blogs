+++
title = "Word 批量转 PDF（Windows 版）"
description = "一次导入大量 Word 文档，按统一的 PDF 选项批量“另存为 PDF”。单文件绿色软件，当前版本 v1.1。"
date = '2026-11-05T09:10:00+08:00'
summary = "一次导入大量 Word 文档，按统一的 PDF 选项批量“另存为 PDF”。调用本机 Word / WPS，版式与手动另存一致；单文件绿色软件，当前版本 v1.1。"
weight = 10
tags = ["Windows", "Word", "PDF", "小工具"]
+++

{{< lead >}}
手动把 Word 转成 PDF，要逐个打开文档、点“另存为”、选 PDF、设置选项、选位置。**Word 批量转 PDF** 把这些步骤批量化：导入文件后设置一次，点「开始转换」即可。
{{< /lead >}}

{{< button href="https://github.com/suntowerlee-gif/sunsoftware/raw/main/Word2PdfBatch/release/Word%E6%89%B9%E9%87%8F%E8%BD%ACPDF.exe" target="_blank" rel="noopener" >}}下载 v1.1（Windows，.exe）{{< /button >}}&nbsp;&nbsp;
{{< button href="https://github.com/suntowerlee-gif/sunsoftware/tree/main/Word2PdfBatch" target="_blank" rel="noopener" >}}说明与源码（GitHub）{{< /button >}}

## 版式与手动另存一致

转换时程序在后台调用本机的 Microsoft Word（或 WPS 文字），使用与“另存为 PDF”相同的导出接口，所以生成的 PDF 版式、字体与手动另存完全一致。

## 功能

**批量导入**

- 多选文件，或导入整个文件夹（可选包含子文件夹）
- 直接把文件或文件夹拖进列表，或拖到 exe 图标上启动
- 支持 `.doc` `.docx` `.docm` `.dot` `.dotx` `.dotm` `.rtf` `.wps`，自动忽略 `~$` 开头的 Word 临时文件

**PDF 选项**（与 Word「另存为 → PDF → 选项」一致）

- 优化方式：标准（联机发布和打印）/ 最小文件大小（联机发布）
- 页面范围：全部 / 指定页码区间
- 发布内容：文档 / 显示标记的文档（含修订和批注）
- 创建书签（使用标题或 Word 书签）、文档属性、辅助功能文档结构标记
- 符合 PDF/A、无法嵌入字体时位图化文本

**保存位置**

- 保存到 Word 源文件所在文件夹，或统一保存到指定文件夹（可保留子文件夹结构）
- 同名 PDF 已存在时：自动重命名 / 覆盖 / 跳过

**其它**

- 每个文件的转换结果显示在列表中，运行日志可导出为 txt；设置自动保存，下次打开沿用
- 带打开密码的文档自动标为失败并跳过，不会卡住；转换时禁用文档中的宏
- 后台 Word 进程用完自动关闭，不会关闭你自己正在编辑的文档

## 运行环境

- Windows 7 / 10 / 11（系统自带 .NET Framework 4.x，无需安装其它运行库）
- 本机已安装并激活 Microsoft Word 2010 及以上版本，或 WPS 文字
- 单个 exe，无需安装，复制到任意位置双击即可运行
- 首次运行从网上下载的 exe 时，Windows 可能提示“已保护你的电脑”，点「更多信息 → 仍要运行」即可

## 软件授权

自 v1.1 起，软件需授权后使用，每台电脑只需激活一次：

1. 首次打开时显示本机 16 位机器码，点「复制」或「发邮件…」发给作者
2. 收到授权码后粘贴到「授权码」框，点「激活」

授权码只对申请时的那台电脑有效，可设置永久或到期日；重装系统或更换系统盘后需要重新获取授权码。授权申请与使用问题请发邮件到 [suntowerlee@gmail.com](mailto:suntowerlee@gmail.com)。

## 英文界面版

功能与中文版 v1.1 相同，界面为全英文，授权码通用。

{{< button href="https://github.com/suntowerlee-gif/sunsoftware/raw/main/Word2PdfBatch_EN/release/WordBatchToPDF.exe" target="_blank" rel="noopener" >}}Download English edition (v1.1){{< /button >}}

## 更新记录

- **v1.1**：加入机器码 + 授权码保护；关于窗口显示授权信息，支持续期；授权到期前 15 天提醒
- **v1.0**：首个版本

## 其它平台

需要在手机上使用？见 [Android 版]({{< ref "software/word-to-pdf-android" >}})。

---

版权所有 © 2026 Suntower Lee。未经作者允许，不得用于商业用途。
