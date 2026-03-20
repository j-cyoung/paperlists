# Robotics 2025 Paperlists

[English README](./README.md)

这个目录用于说明已经正式接入 `paperlists` 主目录的 2025 年机器人方向论文元数据。

## 文件

- [`../ijrr/ijrr2025.json`](../ijrr/ijrr2025.json)：124 条 IJRR 2025 记录
- [`../icra/icra2025.json`](../icra/icra2025.json)：1604 条 ICRA 2025 记录
- [`../iros/iros2025.json`](../iros/iros2025.json)：1985 条 IROS 2025 记录

## 公开来源

- `IJRR 2025`：使用 Crossref 的期刊 works 接口，按 ISSN `0278-3649` 和 2025 年过滤
- `ICRA 2025`：先用 DBLP proceedings 页面精确枚举 DOI，再用 OpenAlex 批量补题目、作者、摘要和落地页，必要时再回退到 Crossref
- `IROS 2025`：先用 DBLP proceedings 页面精确枚举 DOI，再用 OpenAlex 批量补题目、作者、摘要和落地页，必要时再回退到 Crossref

## 归一化规则

- 输出格式遵循现有 `paperlists` 风格：使用扁平 JSON 数组，包含 `id`、`title`、`author`、`abstract`、`site`、`doi` 等字段
- `ICRA` 和 `IROS` 统一使用 `track="main"`、`status="Published"`，因为这里采用的公开来源没有稳定暴露 poster/oral 之类的机器可读标注
- `IJRR` 使用 `track="journal"`、`status="Published"`

## 已知缺口

- `IJRR 2025`：有 3 条记录在上游公开元数据中没有摘要
- `ICRA 2025`：有 28 条记录在上游公开元数据中没有摘要
- `IROS 2025`：有 4 条记录在上游公开元数据中没有摘要

## 重新生成

请在项目根目录运行。

统一使用共享抓取入口：

```bash
python ./tools/fetch_paperlist_metadata.py \
  --venues ijrr icra iros \
  --years 2025
```

脚本会先把生成结果写到 `./store/robotics_2025_metadata_20260311/`，确认无误后再提升到 `./paperlists/...` 中作为正式仓库版本。
