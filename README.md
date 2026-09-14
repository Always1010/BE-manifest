# BE Manifest

这个仓库用于管理同一工作区中的多个独立 Git 仓库。

`default.xml` 是 Google Repo 工具使用的 Manifest。它只记录仓库地址、本地目录和跟踪分支，不包含各项目的源码，也不会替代各项目自身的 Git 仓库。

## 当前管理的仓库

| 本地目录 | GitHub 仓库 | 跟踪分支 |
| --- | --- | --- |
| `AutoScrollPDF` | `Always1010/AutoScrollPDF` | `master` |
| `BilibiliAudioPlayer` | `Always1010/BilibiliAudioPlayer` | `main` |
| `BiliBiliToolBox` | `Always1010/BilibiliToolBox` | `main` |
| `BreakReminder` | `Always1010/BreakReminder` | `main` |
| `CaptionRoll` | `Always1010/CaptionRoll` | `main` |
| `NotesAnywhere` | `Always1010/NotesAnywhere` | `main` |

## 将本仓库上传到 GitHub

在 GitHub 创建空仓库后，为这个本地仓库设置远程地址并推送：

```bash
git remote add origin https://github.com/Always1010/BE-manifest.git
git push -u origin main
```

如果远程仓库名称不同，请相应替换 URL。

## 将来使用 Repo 初始化工作区

请在一个新的空目录中运行，不要直接在已经包含这些项目的工作区中测试：

```bash
repo init -u https://github.com/Always1010/BE-manifest.git
repo sync
```

常用命令：

```bash
repo status
repo sync
repo forall -c 'git status'
```

## 更新管理清单

- 新增项目：在 `default.xml` 中增加一个 `<project>`。
- 删除项目：删除对应的 `<project>`。
- 修改本地目录：调整 `<project>` 的 `path`。
- 修改跟踪分支：调整 `<project>` 的 `revision`。

Manifest 中不要保存密码、访问令牌、私钥或 `.env` 内容。

## 当前状态记录

最近一次本地与 GitHub 检查结果保存在 [`AUDIT-2026-09-14.md`](AUDIT-2026-09-14.md)。`default.xml` 采用分支跟踪模式，不会锁定到检查时的本地提交。
