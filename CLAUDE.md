# Website Project Rules

## Timeline 同步规则 (CRITICAL)

所有项目详情页中的 Timeline 部分 **必须** 从 `_data/profile.yml` 的 `recent_work.items` 动态读取，使用 Liquid 模板按 `project` 字段过滤。

**唯一数据源**: `_data/profile.yml` → `recent_work.items`

**规则**:
- 首页 Recent Work、Archive 页 Recent Work、每个项目详情页的 Timeline **全部从同一数据源读取**
- 更新 `profile.yml` 中的 `recent_work.items` → 所有页面自动同步
- **绝对不允许** 在详情页中硬编码 Timeline 条目
- 每条 recent_work item 必须有 `project` 字段，用于关联到对应项目
- 项目详情页使用以下 Liquid 代码读取:

```liquid
{% assign rw_items = site.data.profile.recent_work.items | where: "project", "项目名" | sort: "sort_date" %}
```

## 项目结构

- 所有项目详情页放在 `_archive/projects/` 下
- 所有项目详情页链接格式: `/archive/项目id`
- 项目封面图放在 `assets/images/archive/`
- 论文/PPT 放在 `assets/papers/`

## 导航

- 导航栏只保留: Home + Archive
- News 和 Publications 暂时隐藏 (display.yml)
