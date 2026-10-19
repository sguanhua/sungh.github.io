# Sungh 的个人主页与博客

网站：<https://sungh314.github.io/>  
技术：GitHub Pages + Jekyll，直接从 `main` 分支根目录发布。无需另租服务器、数据库或安装 WordPress。

## 首次上传源码包

如果当前仓库还是空的：

1. 解压 `sungh314-github-pages-blog.zip`，进入解压后的文件夹。
2. 在本仓库点击 **uploading an existing file**（已有文件时使用 **Add file → Upload files**）。
3. 将解压后的源码文件和 `_layouts`、`_posts` 文件夹一起拖入上传区域。上传的是源码内容，不是 ZIP 文件，也不要把外层 `sungh314.github.io` 文件夹作为网站根目录。必须保留子目录结构。
4. 提交到 `main`。确认仓库根目录能看到 `index.html` 和 `_config.yml`，`_layouts` 中有 `default.html`，`_posts` 中有开站文章。
5. 进入 **Settings → Pages → Build and deployment**，选择 **Deploy from a branch → main → /(root)**，保存。
6. 在 **Actions** 等待 `pages build and deployment` 成功，再从 Pages 设置页打开网站。

如果习惯使用 Git，也可以在解压后的源码目录中执行以下命令，把本地代码推送到这个新建的空仓库。GitHub 的身份验证请使用自己的正常登录方式，不要把密码或令牌写入文件：

```bash
git init -b main
git add .
git commit -m "Create personal homepage and blog"
git remote add origin https://github.com/Sungh314/sungh314.github.io.git
git push -u origin main
```

首次推送后同样需要在仓库 **Settings → Pages** 中选择发布分支和根目录。

## 日常写文章：只需要添加一个 Markdown 文件

1. 进入本仓库的 `_posts` 文件夹。
2. 点击 **Add file → Create new file**。
3. 文件名写成 `年-月-日-英文短名.md`，例如 `2026-10-20-a-day-out.md`。日期不能晚于当前日期；文件名日期决定文章归属日期，`date` 字段可进一步指定时区和时间。
4. 复制下面的模板，修改标题、简介、日期与正文。
5. 点击 **Commit changes**，提交到 `main` 分支。等待 Pages 构建完成后，文章会自动出现在首页、文字列表和 RSS 中。

```markdown
---
title: 文章标题
description: 一句话简介，显示在文章列表中。
date: 2026-10-20 10:00:00 +0800
---

从这里开始写正文。

## 小标题

普通段落、列表、链接都可以使用 Markdown。

![清楚描述画面内容的替代文字](/images/2026/example.jpg)
```

文章的固定地址是 `/notes/英文短名/`。发布后尽量保持文件名中的英文短名稳定，避免旧链接失效。

## 编辑现有内容

| 想改的内容 | 修改文件 |
| --- | --- |
| 网站名称、简介、地址 | `_config.yml` |
| 首页文字与结构 | `index.html` |
| 关于页 | `about.md` |
| 文章 | `_posts/` 中对应的 `.md` 文件 |
| 相册照片与说明 | `photos.html` 顶部的 `photos` 列表 |
| 颜色、字号、间距、移动端样式 | `style.css` |
| 全站导航、页脚、文章通用外观 | `_layouts/default.html` |

首篇《这里，慢慢更新》和关于页是开站时准备的起始文案，可以直接改成自己的文字。相册目前没有真实照片，也没有使用别人的照片冒充作品。

## 上传照片

建议先导出网页用副本：长边约 1600–2400 像素，使用 JPEG 或 WebP，尽量控制在几百 KB，保留原始照片在自己的备份中。发布前检查是否需要去掉 EXIF 中的位置等信息。

在仓库中新建 `images/2026/.gitkeep`，即可建立照片目录；进入该目录后使用 **Add file → Upload files** 上传照片。不要把原片直接批量提交进 Git 历史。

然后把 `photos.html` 顶部的 `photos: []` 替换成：

```yaml
photos:
  - src: /images/2026/example.jpg
    alt: 对画面内容的简短描述
    caption: 照片标题或说明
  - src: /images/2026/another.jpg
    alt: 另一张照片的画面内容
    caption: 另一段说明
```

`photos` 列表下方的 HTML 不需要改。缩进使用空格，包含冒号的文字可用英文双引号包裹。

## 草稿与可见性

这个仓库与发布的网站都是公开的。不要提交密码、令牌、身份证件或不准备公开的照片。即使 `_drafts` 不被 Jekyll 发布，其中的源文件也会在公开仓库中可见；私密草稿请保存在本地。

本站没有接入评论、第三方字体、第三方访问统计或外部图片服务。GitHub 作为托管服务仍可能保留访问日志。

## 发布与排错

- 设置入口：**Settings → Pages**。
- 发布源：**Deploy from a branch → main → /(root)**。
- 每次提交后，在 **Actions** 查看 `pages build and deployment` 是否完成。
- 首次发布可能需要几分钟。看到成功部署后再刷新网页。
- 如果出现 404：先检查 Pages 的分支和目录，再检查是否有 `index.html`；如果构建失败，打开 Actions 的失败日志。
- 不要添加 `.nojekyll`，本项目需要 Jekyll 处理模板、文章和 RSS。

## 备份与迁移

源码和历史保存在 Git 仓库中。可以使用 **Code → Download ZIP** 下载当前版本，也可以在自己的电脑执行：

```bash
git clone https://github.com/Sungh314/sungh314.github.io.git
```

定期保留自己的副本。未来更换主题、绑定域名或迁往其他静态托管平台，不需要重新撰写 Markdown 正文。

文字和照片默认保留作者权利；公开可见不等于授权他人自由转载。
