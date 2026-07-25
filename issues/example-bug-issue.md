# Issue 记录（示例：构建偶发失败）

## 基本信息

- 仓库：Jokerw87/github-work-materials
- Issue 链接：https://github.com/Jokerw87/github-work-materials/issues/2
- 负责人：黄公子
- 状态：已解决
- 记录日期：2026-07-25

## 问题描述

CI 中构建任务偶发失败，报错 `npm ci` 阶段出现 `ETIMEDOUT`，重试后又能通过，无稳定复现规律。

## 复现步骤

1. 向 main 推送任意提交触发 CI
2. 观察 build 任务，约 1/5 概率在依赖安装阶段超时

## 排查过程

- 本地执行 `npm ci` 稳定通过，排除代码问题
- 查看 CI 日志，超时集中在拉取某私有 registry 时
- 确认 CI 运行机出口到该 registry 的网络存在抖动

## 结论与建议

将私有依赖改为缓存 + 镜像源，并对 `npm ci` 增加超时与重试；必要时切换 CI 运行机区域。
