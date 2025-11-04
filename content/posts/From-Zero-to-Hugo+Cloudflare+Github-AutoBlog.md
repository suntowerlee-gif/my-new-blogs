+++
date = '2025-11-04T22:45:12+08:00'
draft = false
title = 'From Zero to Hugo+Cloudflare+Github AutoBlog'

+++

# 🚀 从零到壹：Hugo + Cloudflare Pages 全自动博客部署记录



本文记录了如何使用 Hugo 静态网站生成器、GitHub Desktop 进行可视化管理，以及 Cloudflare Pages 实现域名托管和全自动部署的完整流程。



## 🎯 最终实现效果



- **本地编写：** 在本地电脑上使用 Markdown 撰写博客。
- **可视化推送：** 使用 GitHub Desktop 可视化工具进行版本管理和推送。
- **全自动发布：** 一旦推送（Push origin），Cloudflare Pages 自动构建并发布网站，无需手动操作服务器。
- **零服务器成本：** 整个过程无需购买和维护传统云服务器。

------



## 阶段一：本地环境搭建与文件准备



这一阶段的目标是创建 Hugo 站点并正确加载主题。



### 1. 创建并初始化 Hugo 站点



Bash

```
# 1. 创建新的站点文件夹
hugo new site new-hugo-blog-local
cd new-hugo-blog-local

# 2. 初始化 Git 仓库（本地版本管理）
git init 
```



### 2. 正确加载主题 (解决 `module not found` 问题)



我们使用 `git submodule` 方式加载主题，注意错误的命令行和配置问题。

Bash

```
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```



### 3. 修正配置文件重复键 (解决 `key theme is already defined` 错误)



由于命令行重复执行或手动添加，导致配置键重复，需要手动修正。

- **操作：** 打开博客根目录下的 **`hugo.toml`** 文件。

- **修正：** 确保文件中 `theme = "ananke"` 只出现**一次**。

  Ini, TOML

  ```
  # 正确的配置示例 (只保留一行 theme)
  baseURL = "/"
  languageCode = "zh-cn"
  title = "我的 Hugo 博客"
  theme = "ananke" 
  ```



### 4. 创建测试文章



运行以下命令创建您的第一篇测试文章，并确保它能被发布。

- **操作：** 打开 `content/posts/welcome-test.md` 文件。
- **修正：** 必须将文件顶部的 `draft: true` **手动改为 `draft: false`**，否则文章不会被部署。

Bash

```
hugo new content posts/welcome-test.md
```

------



## 阶段二：GitHub Desktop 可视化管理与推送



这一阶段的目标是安全地将本地文件上传到 GitHub，并建立远程关联。



### 1. GitHub 仓库准备



- 在 GitHub 网站上，**创建**一个**全新的、空白的**远程仓库（例如 `my-cloudflare-blog`）。



### 2. 关联本地文件夹 (解决“文件夹不为空”问题)



由于本地文件夹已经存在 Hugo 文件，不能使用常规的 **Clone**。我们使用 **“添加现有本地仓库”** 的方式接管文件夹。

- **操作 1 (添加本地仓库)：**
  - 打开 GitHub Desktop。
  - 点击 **File** -> **Add local repository...**。
  - 选择您的本地 Hugo 文件夹 (`new-hugo-blog-local`)。
- **操作 2 (关联远程仓库 URL)：**
  - 在 GitHub Desktop 中，点击 **Repository** -> **Repository Settings** -> **Remote**。
  - 在 URL 框中，粘贴您在 GitHub 上创建的空白仓库的 URL 地址。



### 3. 首次推送文件



- **操作：**
  - 在 GitHub Desktop 的 **"Changes"** 标签页。
  - 输入 **Commit 摘要**（例如：“Initial upload of complete Hugo site”）。
  - 点击 **Commit to main**，然后点击 **Push origin**。

------



## 阶段三：Cloudflare Pages 自动化部署



这一阶段的目标是将您的 GitHub 仓库连接到 Cloudflare 的全球 CDN。



### 1. 创建 Pages 项目



- 登录 Cloudflare Dashboard，导航到 **Pages**。
- 点击 **“Create a project”** -> **“Connect Git”**，并选择您刚刚推送的 GitHub 仓库。



### 2. 构建配置 (Build Settings)



确保以下配置正确，以让 Cloudflare 成功运行 Hugo：

| **设置项**                 | **值**   |
| -------------------------- | -------- |
| **Framework preset**       | `Hugo`   |
| **Build command**          | `hugo`   |
| **Build output directory** | `public` |



### 3. 部署和绑定域名



- 点击 **“Deploy site”**。
- 部署成功后，进入 **“Custom domains”** 绑定您在 Cloudflare 托管的域名。



### ⚠️ 解决部署失败问题



如果部署失败，通常是因为 `hugo.toml` 或 `.md` 文件有格式错误。

- **操作：** 点击 **Failed 部署记录**，滚动到 **构建日志底部**查找具体的 `Error:` 信息。
- **修正：** 修复本地的 `.md` 或 `.toml` 文件后，回到 GitHub Desktop，**Commit & Push** 一次，Cloudflare 会自动重试部署。

------



## 总结：日常维护工作流



一旦搭建成功，您日常发布博客的流程将简化为以下三步：

1. **写作：** 在本地 `content/posts/` 文件夹中编写 `.md` 文件，并确保 `draft: false`。
2. **推送：** 打开 **GitHub Desktop** -> **Commit** -> **Push origin**。
3. **发布：** **Cloudflare Pages 全自动完成构建和上线。** (无需等待，新的文章很快就会在您的域名上显示。)
