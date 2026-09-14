# Wangrui Gong · 龚王睿

I'm finishing a Master of Information Systems Management (Business Intelligence & Data Analytics) at
Carnegie Mellon and graduate in December 2026. My bachelor's degree is in International Economics &
Trade from Shanghai International Studies University, taught in Japanese. I'm looking for data analyst
and product analyst roles that start in early 2027.

gongwangrui@gmail.com · [LinkedIn](https://www.linkedin.com/in/wangruigong) · Pittsburgh, PA

## Projects

### [Power outage forecasting and generator placement](https://github.com/wangruig-lang/MLPS_Final_Project)

Team project for CMU 95-828 Machine Learning for Problem Solving, spring 2026. Python, scikit-learn,
PyTorch.

The model forecasts hourly power outages in 83 Michigan counties 24 and 48 hours ahead, and the
forecasts decide where 5 backup generators go. I built most of the models, did the exploratory
analysis and feature engineering, and ran the deep-learning experiments.

- The 24-hour forecast has an RMSE of 92.17. The historical-average baseline has 113.42, so the error
  is 18.8% lower.
- The generator plan covers 66.4% of predicted outage-hours. Placing the generators in the five
  most populous counties covers 51.7%.
- I tuned loss functions for a 3-layer LSTM, with and without a GCN branch, for three days before I
  tried gradient boosting. `HistGradientBoostingRegressor` on the same features and split trained in
  four seconds and beat the best LSTM configuration by 37 RMSE points. Changing the loss did not move
  the LSTM's rate-space validation RMSE (0.0099 ± 0.002 in every configuration); the limit was in the
  features and architecture. I now fit a tabular baseline before any sequence model.
- The models first looked overfit because a chronological 80/20 split put one large June storm
  entirely in the validation set (train mean 32.7, validation mean 87.9). With an interleaved split,
  log-space validation RMSE fell from 1.38 to 1.02, and we recomputed every baseline.
- The placement plan's regret is 0–0.41% under ±20% forecast noise and 0% under ±6-hour timing
  shifts. If the storm's center lands somewhere else, regret rises to 98–99.9%.

`docs/PROGRESS.md` in the repo logs every experiment, including the failed ones.

### AI-readiness assessment (private repository)

A six-person project incubated at CMU and advised by faculty. The repository is private under the
team's access rules.

I maintain the item bank: 900+ items in English and Chinese across six capability dimensions, 30+
authoring and review standards, and the CI checks that enforce them. I also designed the internal
review workbench (try-it, browse and dashboard modes; per-module annotation; dimension and difficulty
re-checks) and led its development. A teammate owns the platform.

To check LLM grading, I had three LLM judges score the same 72 answers independently. They agreed on
57% of rubric criteria. The disagreements traced back to one of our authoring rules, which required
padded rubric points. After we changed the rule, agreement on the same answers was 68%. The share of
answers sent to human review stayed about the same (24% before, 25% after).

### Deep learning coursework (private repositories)

CMU 11-785 Introduction to Deep Learning, five assignments: frame-level phoneme classification, face
classification, face verification with ArcFace, and speech recognition with CTC and with attention.
Top 10% on all five class Kaggle leaderboards; A+ in the course. The repositories are private because
they contain graded assignments.

## Experience

### ByteDance · TikTok LIVE · Business Analyst Intern

Beijing · June–August 2026

I supported agency and creator operations for Japan, Korea and Taiwan. Most of the team was in Tokyo,
and we worked in English.

- After a targeted banner-delivery strategy rolled out to all users, operations reported a drop in
  campaign-page impressions, and the team considered rolling the strategy back. I handled the
  impression analysis. I first separated out a page-display bug, which engineering fixed. I then
  re-cut the data by week, by two-week period and by flagship campaign. The drop came from one
  flagship campaign's normal lifecycle decay, and engagement and revenue did not fall. The team kept
  the strategy and added an exemption list for flagship campaigns.
- My lead and the Taiwan market team set the framework for the Q3 Taiwan agency-incentive review, and
  I implemented it. I wrote a script that checks four eligibility conditions (first-time membership,
  prior monthly revenue of $30 or less, a 15-day cooling-off window, a 7-day trial exemption) for 200+
  claimed creators against six months of records for all creators. It found both missed claims and
  ineligible ones. Claim coverage rose from 40% to about 70% and stayed there.
- One weekly report showed total revenue below the revenue of the claimed cohort. A warehouse field
  had a description that matched the business definition, but its logic selected a narrower group. I
  rebuilt the cohort with daily-grain queries and reviewed the extra creators with the market team.
  After that, I traced every field to its source and checked results at the lowest grain before
  sending a report.
- The high-value agency dashboard depended on a query someone ran by hand every day. I replaced it
  with a scheduled page that validates its own data, so operations staff in the three markets could
  pull numbers themselves. This saved about 6 hours a week. I also built a bot for campaign records
  that checks for missing fields, messages the owner, writes the status back, and escalates after 24
  and 48 hours. It handles about 150 records a day, and on-time completion rose from 60% to 90%.

### Joyson Safety Systems · Data Analyst Intern

Shanghai · February–May 2024

I worked on production-line monitoring. Thirty data sources (SQL databases, Excel ledgers and line
systems) used different field definitions, product codes and time units, so planned and actual output
could not be compared. I mapped them to shared definitions at shift, day and week level. I then set
anomaly rules for 100+ metrics across 200+ production lines, using a historical baseline, a
normal-variation band and a persistence check. Thresholds were adjusted for seasonality, and an alert
fired only after consecutive breaches, which reduced false alarms. Each alert can be broken down by
line, time window and product to locate the source.

### JD Logistics · Data Analyst Intern

Beijing · July–August 2023

I built a merchant tiering model on four dimensions: sales, traffic, growth potential and compliance
risk. I set the weights by grid search within ranges based on business knowledge, then checked with
Spearman rank correlation that the tiers stayed stable across periods. I also built a churn model on
80k+ behavioral records, using trend features such as period-over-period change and time-ordered
train/validation splits to avoid leakage.

## Tools

Python (pandas, scikit-learn, XGBoost, PyTorch) · SQL · Tableau · Power BI · Git and GitHub Actions

Chinese (native) · English (fluent) · Japanese (JLPT N2)

## 中文

我在卡内基梅隆大学读信息系统管理硕士（商业智能与数据分析方向），2026 年 12 月毕业；本科毕业于上海外国语
大学国际经济与贸易专业，用日语授课。正在找 2027 年初入职的数据分析、产品分析岗位。

### 项目

[停电预测与发电机投放](https://github.com/wangruig-lang/MLPS_Final_Project)（CMU 95-828 课程团队项目，
2026 年春）。模型预测密歇根州 83 个县未来 24 和 48 小时的每小时停电数，再根据预测决定 5 台备用发电机放在
哪些县。我负责大部分建模、探索性分析、特征工程和深度学习实验。

- 24 小时预测的 RMSE 为 92.17，历史均值基线为 113.42，误差低 18.8%。
- 发电机方案覆盖 66.4% 的预测停电量；放在人口最多的 5 个县，覆盖 51.7%。
- 我先花三天调 3 层 LSTM（带或不带 GCN 分支）的损失函数，之后才试梯度提升。同样的特征和数据划分下，
  HistGradientBoostingRegressor 训练 4 秒，RMSE 比最好的 LSTM 配置低 37。换哪种损失函数，LSTM 在比率
  空间的验证 RMSE 都停在 0.0099 ± 0.002，瓶颈在特征和模型结构。现在我会先跑表格模型的基线。
- 模型一开始看起来过拟合，原因是按时间 80/20 划分时，6 月的一场大风暴全部落在验证集（训练集均值 32.7，
  验证集均值 87.9）。改成交错划分后，对数空间的验证 RMSE 从 1.38 降到 1.02，所有基线都重算了一遍。
- 预测误差 ±20% 时，方案的后悔值为 0–0.41%；时间偏移 ±6 小时时为 0；风暴中心位置预测错时，后悔值升到
  98%–99.9%。

AI 能力测评项目（CMU 孵化，教授指导，6 人团队，仓库不公开）。我维护题库（中英双语 900 多道题，覆盖 6 个
能力维度）、30 多份出题和审题标准，以及执行这些标准的 CI 检查；我设计了内部审题工作台并主导开发，平台本身
由同学负责。为了检验大模型评分，我让三个大模型评分者独立给同一批 72 份答案打分，评分点一致率为 57%。分歧
来自我们自己的一条出题规则，它要求评分卡凑满给分点。改掉这条规则后，同一批答案的一致率为 68%；转人工复核
的比例基本没变（改前 24%，改后 25%）。

11-785 深度学习课程作业：音素分类、人脸分类、人脸验证（ArcFace）、CTC 语音识别和 attention 语音识别，
五次课程 Kaggle 竞赛都进入前 10%，课程成绩 A+。课程作业不公开。

### 实习

字节跳动 TikTok LIVE，商业分析实习生，北京，2026 年 6–8 月。支持日本、韩国、台湾三地的公会与主播运营；
团队多数同事在东京，日常用英文协作。

- banner 精准推流策略推全后，运营发现活动页曝光下降，团队考虑整体回滚。我负责其中的曝光归因。先把页面
  看不到这个问题单独拆出来，确认是基建缺陷，交给技术修复；再按周、双周和头部活动三个粒度重新切数据。下降
  只出现在一个头部活动上，属于活动本身的生命周期衰减，参与度和营收没有下降。团队保留了策略，并加了头部
  活动豁免名单。
- 台湾 Q3 拉新激励复盘的框架由 leader 和台湾业务同学确定，我负责实现。我把首次入会、入会前单月营收不超过
  30 美元、15 天后悔期、7 天试播豁免四条规则写成核验脚本，比对 200 多位申报主播和全量主播近半年的记录，
  找出漏报和不符合条件的申报。申报覆盖率从 40% 升到约 70%，之后保持稳定。
- 一份周报里，大盘营收低于申报口径的营收。原因是数据库里一个现成字段的描述和业务口径一致，筛选逻辑却更窄。
  我用日粒度查询重建了新人名单，把多出来的主播交给台湾业务同学确认。之后每份报告发出前，我都先追溯字段
  来源，再做最小粒度核对。
- 高价值公会看板原来每天要有人手动跑查询。我把它改成定时刷新的页面，并加了兜底校验，三地运营可以自己
  取数，每周省下约 6 小时。我还做了活动信息催办机器人，检查缺失字段、通知负责人、回写状态，超过 24 小时
  和 48 小时分级提醒。它每天处理约 150 条记录，信息补全及时率从 60% 升到 90%。

均胜安全系统，数据分析实习生，上海，2024 年 2–5 月。30 个数据源（SQL 数据库、Excel 台账、产线系统）的
字段定义、产品编码和时间粒度不一致，计划产量和实际产量没法对比。我把它们统一到班次、天、周三级口径，再为
200 多条产线的 100 多项指标设了异常规则：历史基准线、正常波动区间和持续性判断，阈值按季节调整，连续超限
才告警，误报明显减少。告警可以按产线、时段和产品下钻，找到偏差来源。

京东物流，数据分析实习生，北京，2023 年 7–8 月。我做了商家四维分层（销售、流量、增长潜力、合规风险），在
业务经验给出的区间内用网格搜索确定权重，再用相邻周期的斯皮尔曼等级相关检验分层是否稳定。我还用 8 万多条
行为数据做了流失预测，特征以环比变化等趋势特征为主，训练集和验证集按时间切分，避免数据泄漏。
