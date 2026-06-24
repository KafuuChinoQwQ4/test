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

统一后的比赛表。AtCoder 的 `adt_*` Daily Training 训练场已从该表中过滤，避免在正式比赛趋势中把练习场计为比赛。

| Column | Description |
|---|---|
| `platform` | 平台名称：`Codeforces` 或 `AtCoder` |
| `contest_id` | 比赛 ID |
| `contest_title` | 比赛标题 |
| `start_time` | 比赛开始时间 |
| `year` | 比赛年份 |
| `contest_family` | 比赛类型，如 `Div.2`、`Educational`、`ABC`、`ARC`、`AGC` |

## `processed/codeforces_rated_users.csv`

Codeforces rated 选手表，来自 `user.ratedList`。

| Column | Description |
|---|---|
| `handle` | Codeforces 用户名 |
| `country` | 用户公开填写的国家/地区 |
| `city` | 用户公开填写的城市 |
| `organization` | 用户公开填写的组织 |
| `rating` | 当前 rating |
| `max_rating` | 历史最高 rating |
| `rank` | 当前 rank 文本 |
| `max_rank` | 历史最高 rank 文本 |
| `rating_band` | 当前 rating 对应段位 |
| `max_rating_band` | 历史最高 rating 对应段位 |
| `contribution` | 贡献值 |
| `friend_of_count` | 被加入好友数量 |

## `processed/codeforces_country_stats.csv`

Codeforces 国家/地区选手统计表。

| Column | Description |
|---|---|
| `country` | 国家/地区 |
| `user_count` | rated 选手数量 |
| `mean_rating` | 当前 rating 平均值 |
| `median_rating` | 当前 rating 中位数 |
| `max_rating` | 该国家/地区当前最高 rating |
| `candidate_master_plus_count` | 当前 rating >= 1900 的选手数量 |
| `candidate_master_plus_ratio` | Candidate Master 及以上选手占比 |

## `processed/codeforces_rating_band_country.csv`

Codeforces Top20 国家/地区 rating 段分布。

| Column | Description |
|---|---|
| `country` | 国家/地区 |
| `rating_band` | Codeforces rating 段位 |
| `user_count` | 该国家/地区该段位人数 |
| `percentage` | 该段位在该国家/地区 rated 选手中的占比 |

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

## `processed/platform_problem_counts.csv`

| Column | Description |
|---|---|
| `platform` | 平台名称 |
| `problem_count` | 该平台题目数量 |

## `processed/difficulty_distribution.csv`

| Column | Description |
|---|---|
| `platform` | 平台名称 |
| `difficulty_band` | 统一难度分组 |
| `problem_count` | 该难度分组下题目数量 |
| `percentage` | 该难度分组在对应平台中的占比 |

## `processed/contest_year_trend.csv`

| Column | Description |
|---|---|
| `platform` | 平台名称 |
| `year` | 年份 |
| `contest_count` | 该平台该年份比赛数量 |

## `processed/codeforces_tag_stats.csv`

| Column | Description |
|---|---|
| `tag` | Codeforces 算法标签 |
| `problem_count` | 该标签题目数量 |
| `mean_rating` | 该标签题目的平均 rating |
| `median_rating` | 该标签题目的 rating 中位数 |
| `mean_solved_count` | 该标签题目的平均通过人数 |
| `median_solved_count` | 该标签题目的通过人数中位数 |
| `easy_count` | Easy 题目数量 |
| `medium_count` | Medium 题目数量 |
| `hard_count` | Hard 题目数量 |
| `unknown_count` | Unknown 题目数量 |

## `processed/leetcode_tag_difficulty_matrix.csv`

| Column | Description |
|---|---|
| `tag` | LeetCode 算法标签 |
| `easy_count` | Easy 题目数量 |
| `medium_count` | Medium 题目数量 |
| `hard_count` | Hard 题目数量 |
| `total_count` | 标签题目总数 |
| `easy_percent` | Easy 占比 |
| `medium_percent` | Medium 占比 |
| `hard_percent` | Hard 占比 |

## `processed/leetcode_low_acceptance_tags.csv`

字段与 `leetcode_tag_acceptance.csv` 一致，但只保留题量不少于 20 的标签，并按平均通过率从低到高排序。

## Difficulty Mapping

| Platform | Easy | Medium | Hard |
|---|---|---|---|
| Codeforces | rating < 1200 | 1200 <= rating < 2000 | rating >= 2000 |
| AtCoder | difficulty < 800 | 800 <= difficulty < 2000 | difficulty >= 2000 |
| LeetCode | level = 1 or EASY | level = 2 or MEDIUM | level = 3 or HARD |

## Codeforces User Rating Bands

| Band | Rating Range |
|---|---|
| `Newbie` | rating < 1200 |
| `Pupil` | 1200 <= rating < 1400 |
| `Specialist` | 1400 <= rating < 1600 |
| `Expert` | 1600 <= rating < 1900 |
| `Candidate Master` | 1900 <= rating < 2100 |
| `Master` | 2100 <= rating < 2300 |
| `International Master` | 2300 <= rating < 2400 |
| `Grandmaster` | 2400 <= rating < 2600 |
| `International Grandmaster` | 2600 <= rating < 3000 |
| `Legendary Grandmaster` | rating >= 3000 |
