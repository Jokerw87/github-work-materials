# CI 构建超时排查记录（示例）

- 时间：2026-07-22
- 仓库 / 分支：Jokerw87/github-work-materials @ main
- 失败检查：build（依赖安装阶段）
- 关联提交：示例 sha

## 现象

build 任务在 `npm ci` 阶段偶发失败，报错：

```
npm error code ETIMEDOUT
npm error network request to https://registry.npmjs.org/xxx failed
```

重试后通常能通过，无稳定复现。

## 排查过程

1. 本地稳定通过，排除依赖树 / 锁文件问题
2. CI 日志显示超时集中在拉取私有 registry 时
3. 确认 CI 运行机到私有源的出口网络存在抖动

## 修复

- 为私有源配置镜像 + 本地缓存
- 对 `npm ci` 增加 `--fetch-timeout` 与重试
- 将构建步骤拆分为「装依赖」「构建」两步，便于定位

## 防止再犯

- 在 CI 中加入依赖缓存命中率监控
- 为网络敏感步骤设置统一重试封装

## 结论

优化后构建稳定性显著提升，偶发超时基本消失。本记录留作 `checks/` 目录的第二个填写范例（与 lint 失败示例互补）。
