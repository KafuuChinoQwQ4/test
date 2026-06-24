# Usage Example

```python
from pathlib import Path
import pandas as pd

root = Path("github_dataset")

problems = pd.read_csv(root / "processed" / "all_problems.csv")
contests = pd.read_csv(root / "processed" / "all_contests.csv")
tag_acceptance = pd.read_csv(root / "processed" / "leetcode_tag_acceptance.csv")
codeforces_users = pd.read_csv(root / "processed" / "codeforces_rated_users.csv")
country_stats = pd.read_csv(root / "processed" / "codeforces_country_stats.csv")
rating_band_country = pd.read_csv(root / "processed" / "codeforces_rating_band_country.csv")
platform_counts = pd.read_csv(root / "processed" / "platform_problem_counts.csv")
difficulty_distribution = pd.read_csv(root / "processed" / "difficulty_distribution.csv")
contest_year_trend = pd.read_csv(root / "processed" / "contest_year_trend.csv")
codeforces_tag_stats = pd.read_csv(root / "processed" / "codeforces_tag_stats.csv")
leetcode_tag_matrix = pd.read_csv(root / "processed" / "leetcode_tag_difficulty_matrix.csv")
low_acceptance_tags = pd.read_csv(root / "processed" / "leetcode_low_acceptance_tags.csv")

print(problems["platform"].value_counts())
print(contests.groupby(["platform", "year"]).size().tail())
print(tag_acceptance.head(10))
print(codeforces_tag_stats.head(10))
print(country_stats.head(10))
```

## Common Analysis

```python
# 三平台题目数量
problem_counts = problems["platform"].value_counts()

# 难度分布
difficulty = problems.groupby(["platform", "difficulty_band"]).size().unstack(fill_value=0)

# LeetCode 低通过率标签
hard_tags = tag_acceptance[tag_acceptance["problem_count"] >= 20].sort_values("mean_acceptance_rate")

# 直接使用已导出的分析结果表
platform_counts.sort_values("problem_count", ascending=False)
difficulty_distribution.pivot(index="platform", columns="difficulty_band", values="percentage")
contest_year_trend.tail(10)
low_acceptance_tags.head(10)

# Codeforces 国家/地区选手统计
country_stats.sort_values("user_count", ascending=False).head(20)
rating_band_country.pivot_table(
    index="country",
    columns="rating_band",
    values="user_count",
    aggfunc="sum",
    fill_value=0,
)
```
