# 🤖 一键自动同步 Fork 仓库（自动检测源仓库 + 代码 + Tags + Releases + 附件）

> 一个基于 GitHub Actions 的自动化工具，帮助你**一键同步你 Fork 的上游仓库**，包括：
>
> ✅ 自动检测源（上游）仓库  
> ✅ 自动识别默认分支（main / master）  
> ✅ 同步最新代码、Tags  
> ✅ 可扩展支持 Releases、附件等（未来版本）  
> ✅ 兼容任意 GitHub Fork 仓库，无需手动修改配置

---

## ✨ 功能特性

| 功能 | 是否支持 | 说明 |
|------|---------|------|
| 🔍 自动检测当前仓库是否为 Fork | ✅ | 如果不是 Fork 仓库，会报错提示 |
| 🔍 自动找出你的源（上游）仓库 | ✅ | 通过 GitHub API 获取 `.parent.full_name` |
| 🌿 自动识别默认分支（main / master / 其他） | ✅ | 无需手动指定，自动适配 |
| 📥 自动同步源仓库的代码和 Tags | ✅ | 包括所有分支最新代码和 Git Tags |
| 🔄 自动合并源仓库到你的默认分支 | ✅ | 使用 `--allow-unrelated-histories` 和 `-X theirs` 策略 |
| 📤 自动推送更新到你的 fork 仓库 | ✅ | 支持使用 Personal Access Token 推送 |
| 🔐 安全可靠，无需暴露敏感信息 | ✅ | 通过 GitHub Secrets 管理 Token |
| 🛠️ 易于部署，开箱即用 | ✅ | 复制 YAML 即可使用 |

> ⚠️ 注意：目前 **不自动同步 Releases / Assets（附件）**，但代码结构清晰，易于扩展。

---

## 🚀 快速开始

### 第一步：Fork 这个项目（可选）

> 如果你只是想在自己已有的 Fork 仓库中引入此自动化同步功能，**不需要 Fork 本项目**，只需要将下面的工作流文件复制到你的 Fork 仓库中即可。

但如果你想研究、改进或二次开发此工具，欢迎 Fork 本项目！

---

### 第二步：将工作流文件添加到你的 Fork 仓库

1. 进入你的 **Fork 仓库**
2. 在仓库根目录下创建文件夹：`.github/workflows/`
3. 在该目录下创建一个工作流文件，例如：  
   **`.github/workflows/sync-fork-auto.yml`**
4. 将上面的完整代码复制粘贴到该文件中

---

### 第三步：设置 GitHub Secret（必须！）

1. 进入你的 Fork 仓库 → **Settings → Secrets and variables → Actions → New repository secret**
2. 添加一个名为：**`MY_GIT_TOKEN`**
3. 值为你的 **Personal Access Token（具有 repo 权限）**
   - 获取地址：https://github.com/settings/tokens
   - 勾选 `repo`
   - 生成后复制并保存到 Secret

---

## 🛠️ 自定义与扩展

- **定时自动同步？**  
  取消注释 `schedule` 部分的 cron 表达式，例如每天同步：
