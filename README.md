# Online Judge Platform Visualization Dataset

本数据集用于“大数据可视化技术”课程作业：**算法竞赛平台数据可视化分析**。

数据来自公开平台接口采集，并在本仓库中整理为原始 JSON、清洗 CSV 和可视化图表。数据覆盖 Codeforces、AtCoder Problems 和 LeetCode 三个平台，可用于分析题库规模、难度结构、算法标签、通过率和竞赛活跃度。

## Dataset Structure

```text
github_dataset/
├── raw/
│   ├── codeforces/
│   │   ├── codeforces_problemset_problems.json
│   │   └── codeforces_contest_list.json
│   ├── atcoder/
│   │   ├── atcoder_problems.json
│   │   ├── atcoder_contests.json
│   │   └── atcoder_problem_models.json
│   └── leetcode/
│       ├── leetcode_problems_all.json
│       └── leetcode_problemset_v2.json
├── processed/
│   ├── all_problems.csv
│   ├── all_contests.csv
│   ├── codeforces_problems.csv
│   ├── atcoder_problems.csv
│   ├── leetcode_problems.csv
│   ├── leetcode_tag_acceptance.csv
│   └── summary.json
├── figures/
└── docs/
```

## Summary

| Item | Count |
|---|---:|
| Total problems | 23824 |
| Codeforces problems | 11245 |
| AtCoder problems | 9035 |
| LeetCode algorithm problems | 3544 |
| Codeforces contests | 2120 |
| AtCoder contests | 6069 |
| LeetCode tags | 69 |

## Recommended Files

如果只想做可视化分析，优先使用 `processed/`：

- `processed/all_problems.csv`: 三平台统一题目表。
- `processed/all_contests.csv`: Codeforces 和 AtCoder 比赛表。
- `processed/leetcode_tag_acceptance.csv`: LeetCode 算法标签通过率统计。
- `processed/summary.json`: 数据规模摘要。

如果需要追溯原始采集结果，使用 `raw/`。

## Data Sources

本数据集不是平台官方发布的单一静态数据集，而是从公开接口采集后整理得到。

| Platform | Source URL | Local File |
|---|---|---|
| Codeforces | https://codeforces.com/api/problemset.problems | `raw/codeforces/codeforces_problemset_problems.json` |
| Codeforces | https://codeforces.com/api/contest.list | `raw/codeforces/codeforces_contest_list.json` |
| AtCoder Problems | https://kenkoooo.com/atcoder/resources/problems.json | `raw/atcoder/atcoder_problems.json` |
| AtCoder Problems | https://kenkoooo.com/atcoder/resources/contests.json | `raw/atcoder/atcoder_contests.json` |
| AtCoder Problems | https://kenkoooo.com/atcoder/resources/problem-models.json | `raw/atcoder/atcoder_problem_models.json` |
| LeetCode | https://leetcode.com/api/problems/all/ | `raw/leetcode/leetcode_problems_all.json` |
| LeetCode | https://leetcode.com/graphql/ | `raw/leetcode/leetcode_problemset_v2.json` |

## Notes

- Codeforces 的 `rating` 和 `tags` 来自题库接口，`solvedCount` 表示通过人数。
- AtCoder 难度来自 AtCoder Problems 的 IRT 模型，不是 AtCoder 官方字段。
- LeetCode 的标签通过率来自 GraphQL 网页接口中的 `topicTags` 和 `acRate`。
- 不同平台难度定义不完全一致，`processed/all_problems.csv` 中的 `difficulty_band` 是为了横向可视化而统一映射得到。

## License and Use

本仓库只整理公开接口返回的数据，原始数据所有权归对应平台或数据源维护者所有。使用时请遵守各平台服务条款，并在报告或项目中注明数据来源。

