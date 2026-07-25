# Issue 记录（示例）

## 基本信息

- 仓库：Jokerw87/github-work-materials
- Issue 链接：https://github.com/Jokerw87/github-work-materials/issues/1
- 负责人：黄公子
- 状态：已解决
- 记录日期：2026-07-25

## 问题描述

克隆仓库后，本地执行 git 命令报 `dubious ownership` 错误，所有操作被拦截。

## 复现步骤

1. 以 `huanghaipeng` 用户打开仓库目录
2. 执行 `git status`

## 排查过程

git 检测到仓库归属 `CodexSandboxOffline`，与当前登录用户不符，触发安全拦截，拒绝读取仓库。

## 结论与建议

执行 `git config --global --add safe.directory <仓库路径>` 将目录加入白名单后即可正常操作。
