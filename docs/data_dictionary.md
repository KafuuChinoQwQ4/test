# Data Dictionary

## `processed/all_problems.csv`

统一后的三平台题目表。

| Column | Description |
|---|---|
| `platform` | 平台名称：`Codeforces`、`AtCoder`、`LeetCode` |
| `problem_id` | 平台内题目 ID |
| `title` | 题目名称 |
| `difficulty_raw` | 原始难度值。Codeforces 为 rating，AtCoder 为 IRT difficulty，LeetCode 为 1/2/3 |
| `difficulty_band` | 统一难度分组：`Easy`、`Medium`、`Hard`、`Unknown` |
| `accepted_count` | 通过人数或 AC 数。Codeforces 有该字段，LeetCode v2 数据中不保留该字段 |
| `submission_count` | 提交数。基础 LeetCode 接口可提供，统一表中部分来源为空 |
| `acceptance_rate` | 通过率百分比。LeetCode v2 可用 |
| `tags` | 算法标签列表。Codeforces 和 LeetCode 可用 |
| `paid_only` | LeetCode 是否为付费题 |
| `contest_id` | AtCoder 题目所属比赛 ID |
| `irt_users` | AtCoder Problems IRT 模型用户数 |
| `is_experimental` | AtCoder Problems 难度模型是否实验性 |

## `processed/all_contests.csv`

统一后的比赛表。

| Column | Description |
|---|---|
| `platform` | 平台名称：`Codeforces` 或 `AtCoder` |
| `contest_id` | 比赛 ID |
| `contest_title` | 比赛标题 |
| `start_time` | 比赛开始时间 |
| `year` | 比赛年份 |
| `contest_family` | 比赛类型，如 `Div.2`、`Educational`、`ABC`、`ARC`、`AGC` |

## `processed/leetcode_tag_acceptance.csv`

LeetCode 算法标签通过率统计表。

| Column | Description |
|---|---|
| `tag` | 算法标签名称 |
| `problem_count` | 该标签下的题目数量 |
| `mean_acceptance_rate` | 该标签题目的平均通过率 |
| `median_acceptance_rate` | 该标签题目的通过率中位数 |
| `easy_count` | 该标签下 Easy 题目数量 |
| `medium_count` | 该标签下 Medium 题目数量 |
| `hard_count` | 该标签下 Hard 题目数量 |

## Difficulty Mapping

| Platform | Easy | Medium | Hard |
|---|---|---|---|
| Codeforces | rating < 1200 | 1200 <= rating < 2000 | rating >= 2000 |
| AtCoder | difficulty < 800 | 800 <= difficulty < 2000 | difficulty >= 2000 |
| LeetCode | level = 1 or EASY | level = 2 or MEDIUM | level = 3 or HARD |

