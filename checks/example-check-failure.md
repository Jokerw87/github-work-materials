# CI 检查失败排查记录（示例）

- 时间：2026-07-20
- 仓库 / 分支：Jokerw87/github-work-materials @ main
- 失败检查：lint（示例）
- 关联提交：示例 sha

## 现象

CI 在 lint 阶段失败，报错：

```
error: trailing whitespace at line 12
```

## 排查过程

1. 本地复现：`npm run lint` → 同样报错
2. 定位：第 12 行末尾有空格
3. 根因：编辑器保存时自动追加了尾随空格

## 修复

- 删除尾随空格
- 提交信息：`fix: remove trailing whitespace`

## 防止再犯

- 增加 `.editorconfig` 统一换行 / 空格规则
- 加 pre-commit hook 在提交前跑 lint

## 结论

修复后 CI 通过，本记录留作 `checks/` 目录的填写范例。
