# 剪贴板历史

原生 Swift + AppKit 菜单栏应用，无第三方依赖，中文界面。

## 构建

需要 macOS、Xcode 26 或更新版本及对应 SDK。首次使用先打开 Xcode 完成组件安装。

```bash
./scripts/build.sh
```

生成 `dist/ClipboardHistory.app`，双击打开即可。脚本不会自动安装或启动应用。

运行内置检查：

```bash
./scripts/build.sh --test
```

完整液态玻璃效果需要 macOS 26；旧系统提供材质回退，尚未逐版本验证。应用使用临时签名供本机构建，公开分发需自行完成 Developer ID 签名和 Apple 公证。

## 功能

- 文字和图片历史、搜索、置顶、暂停记录、删除。
- 文本、图片、链接、代码、Markdown、颜色分类。
- VS Code“2026 深色”风格代码高亮、Menlo 15 字号、彩色括号。
- Markdown 排版预览、源码切换和代码块高亮。

## 操作

**Option + Command + V（⌥⌘V）** 在鼠标附近呼出。↑↓ 选择，回车复制并返回之前的应用，然后在目标应用按 ⌘V 粘贴。菜单栏可打开或退出应用。

普通历史最多 200 条，置顶记录不会自动淘汰。单条文字上限 2 MB，PNG 图片上限 12 MB。轻量语法识别不等同于 VS Code 完整语言服务；代码前 120,000 个 UTF-16 单元着色，剩余内容完整显示。

## 本地数据与隐私

历史：`~/Library/Application Support/GlassClipboard/history.json`，以本地 JSON 保存，无应用级加密。没有联网功能，Markdown 图片引用不会自动加载。

带保密、临时标记的剪贴板内容会跳过；无标记的密码等普通文本仍可能记录，可使用“暂停记录”。

bundle identifier：`local.glassclipboard`。更新前先退出旧版本，以继续使用现有历史并避免快捷键冲突。

## 上传 GitHub

本目录可单独作为一个 GitHub 仓库。上传 `Sources/`、`scripts/`、`docs/`、`README.md` 和 `.gitignore`，无需上传 `build/`、`dist/` 或个人历史。

完整源码位于 `Sources/ClipboardHistory/main.swift`；中文使用说明见 `docs/`。
