# Source Notes

## Codeforces

Codeforces 数据来自官方 API：

- `problemset.problems`: 题目信息、标签、rating、通过人数。
- `contest.list`: 比赛列表。

接口文档：https://codeforces.com/apiHelp

## AtCoder Problems

AtCoder 数据来自 AtCoder Problems 公开资源接口：

- `problems.json`: 题目列表。
- `contests.json`: 比赛列表。
- `problem-models.json`: 基于 IRT 模型估计的题目难度。

资源入口：https://kenkoooo.com/atcoder/resources/

注意：`problem-models.json` 中的 difficulty 是 AtCoder Problems 维护的估计难度，不是 AtCoder 官方直接给出的题目字段。

## LeetCode

LeetCode 数据分为两个来源：

- `https://leetcode.com/api/problems/all/`: 题目基础统计，包括难度、AC 数、提交数。
- `https://leetcode.com/graphql/`: 网页 GraphQL 接口，用于补充算法标签和 `acRate`。

注意：LeetCode 数据是网页公开接口采集结果，不是 LeetCode 官方发布的静态数据集。

## Local Processing

清洗流程将三平台题目统一为公共字段，并生成：

- `all_problems.csv`
- `all_contests.csv`
- `leetcode_tag_acceptance.csv`
- `platform_problem_counts.csv`
- `difficulty_distribution.csv`
- `contest_year_trend.csv`
- `codeforces_tag_stats.csv`
- `leetcode_tag_difficulty_matrix.csv`
- `leetcode_low_acceptance_tags.csv`

主要清洗逻辑：

1. 统一题目 ID、标题、平台名称。
2. 将不同平台难度映射为 `Easy / Medium / Hard / Unknown`。
3. 合并 AtCoder 题目表和难度模型。
4. 基于 LeetCode `topicTags` 和 `acRate` 计算标签级平均通过率。
5. 基于比赛标题或 ID 识别 Codeforces/AtCoder 比赛类型。
6. 从主表派生题量、难度分布、年度趋势、标签统计等 analysis-ready CSV，方便直接绘图。
