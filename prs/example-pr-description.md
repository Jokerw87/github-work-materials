# PR 描述（示例）

## 这个 PR 做了什么

为仓库补充 issue / PR / 故障复盘等模板，并新增两个排查记录示例，统一团队记录格式。

## 改动点

- 新增 `templates/bug-report.md`、`templates/pr-description.md`、`templates/postmortem.md`
- 新增 `issues/example-bug-issue.md`、`prs/example-pr-description.md`
- 新增 `checks/example-build-timeout.md`

## 关联

- 关联 Issue：#2（构建偶发失败）

## 自测

- [x] 本地冒烟通过
- [x] 新增示例均符合模板结构
- [ ] 文档已同步

## 测试建议

重点检查新增模板在复制后是否可直接填空使用，示例中的链接与 sha 是否为占位。

## 风险 / 注意

- 兼容性：纯文档变更，无代码风险
- 回滚：`git revert <本 PR sha>`
