# Wangrui Gong · 龚王睿

Master of Information Systems Management (Business Intelligence & Data Analytics) at **Carnegie Mellon**,
graduating December 2026. Before that, International Economics & Trade — studied in Japanese — at
Shanghai International Studies University.

Most of what I do sits between a model and a decision. Encoding a messy incentive rule into
something checkable, separating a strategy's effect from a campaign's natural decay, getting thirty
disagreeing data sources onto one definition, or deciding where five generators go given a forecast
you don't fully trust — that middle part is the work I like.

📮 gongwangrui@gmail.com · [LinkedIn](https://www.linkedin.com/in/wangruigong) · Pittsburgh, PA

---

## [Power outage forecasting & generator placement](https://github.com/wangruig-lang/MLPS_Final_Project)

Forecast hourly power outages across 83 Michigan counties at 24h/48h, then use those forecasts to
place 5 backup generators. `Python` · `scikit-learn` · `PyTorch`

Two numbers I'd point at: 24h RMSE of **92.17 vs. 113.42** for the historical-average baseline
(−18.8%), and a generator plan that mitigates **66.4%** of predicted outage-hours against **51.7%**
for the obvious "put them where the people are" heuristic.

Three things I learned the hard way, which are the actual reason this repo is worth reading:

- **I spent three days tuning loss functions on a 3-layer LSTM + GCN before trying gradient
  boosting.** `HistGradientBoostingRegressor`, same features, same split, beat it by 37 RMSE points
  in four seconds of training. Across every loss configuration the LSTM's rate-space validation RMSE
  converged to 0.0099 ± 0.002 — the ceiling was the architecture, not the loss. I now run the tabular
  baseline first, always.
- **What looked like overfitting was distribution mismatch.** A chronological 80/20 split had put one
  large June storm entirely in validation (train mean 32.7, val mean 87.9). Switching to an
  interleaved split dropped log-space validation RMSE from 1.38 to 1.02 and invalidated every
  baseline number we'd recorded up to that point.
- **The placement plan has an honest failure mode, and I published it.** It shrugs off ±20% forecast
  noise (0–0.41% regret) and ±6h timing shifts (0%), but a relocated storm epicenter costs 98–99.9%.
  The decision depends on getting the location right, not the intensity — so I put that in the README
  instead of only reporting the robustness that flattered it.

`docs/PROGRESS.md` in that repo is the full experiment log, including every configuration that failed.

---

## Other work

**AI-readiness assessment** *(private — team project, content under owner gating)*
A faculty-advised, CMU-incubated project; six of us. I own the item-bank side: 900+ bilingual items
across six capability dimensions, 30+ authoring and review standards, and CI quality gates. I also
designed and led development of the internal review workbench (try-it / browse / dashboard modes,
per-module annotation, dimension and difficulty re-checks); a teammate owns the platform itself.
The hard problem is **LLM grading consistency**. Nobody had checked whether two graders using the
same rubric give the same answer the same score, so I ran a blind test: three LLM judges, 72 answers.
Criterion-level agreement was **57%**. The root cause was one of our own authoring rules, which forced
padded rubric points. After rewriting it, agreement on the same answers rose to **68%**. The
human-escalation rate didn't move, and the write-up says so.

**Deep learning coursework** *(private — CMU 11-785)*
Frame-level phoneme classification, face classification and verification with ArcFace, and two
speech recognition systems (CTC and attention-based) — **top 10% in all five class Kaggle
competitions, A+ in the course**. Repos stay private: they're graded assignments with reference
solutions.

---

## Experience

**ByteDance · TikTok LIVE** — Business Analyst Intern · Shanghai · Jun–Aug 2026
Agency and creator analytics for Japan, Korea and Taiwan, working in English with a mostly
Tokyo-based team.

- After a targeted banner-delivery strategy went global, ops flagged a drop in campaign-page
  impressions and the team considered rolling it back. I owned the impression attribution. I split
  off a separate page-display bug (engineering fixed it), then re-cut the data by week, bi-week and
  flagship campaign. The decline sat in one flagship campaign's lifecycle decay, and engagement and
  revenue held. **The strategy stayed**, with a flagship-campaign exemption list added.
- Implemented the Q3 Taiwan agency-incentive review (the framework came from my lead and the market
  team). I encoded four eligibility conditions (first-time membership, sub-$30 prior monthly revenue,
  a 15-day cooling-off window, a 7-day trial exemption) into a script that checked 200+ claimed
  creators against six months of full-population records, catching both missed and ineligible
  claims. Claim coverage went **40% → 70%** and held.
- A weekly report showed total revenue *below* the claimed-cohort revenue. The cause was a warehouse
  field whose description matched the business definition but whose logic was narrower. I rebuilt
  the cohort from daily-grain queries, reconciled the difference with the market team, and now trace
  every field to its source and check results at the lowest grain before a report ships.
- Turned the high-value agency dashboard, a query someone ran by hand every day, into a scheduled
  page with fallback validation, so ops in three markets could self-serve (**~6 hours/week** back).
  A companion bot chases incomplete campaign records — field validation, owner outreach, status
  write-back, 24h/48h escalation — at **150 records/day**, lifting on-time completion **60% → 90%**.

**Joyson Safety Systems** — Data Analyst Intern · Shanghai · Feb–May 2024
Production-line monitoring. The real problem wasn't modeling, it was that **30 data sources** —
SQL, Excel ledgers, line systems — disagreed on field definitions, product codes and time
granularity, so planned-vs-actual variance couldn't be computed at all. I reconciled them onto one
base (shift / day / week), then built anomaly detection over **100+ metrics** across **200+
production lines**: historical baseline, normal-variation band and a persistence test, with
seasonal threshold correction and a consecutive-breach rule to keep false alarms down. Drill-down
by line, time window and product means an alert points at a cause, not just a number.

**JD Logistics** — Data Analyst Intern · Beijing · Jul–Aug 2023
Built a merchant tiering model on four dimensions (sales, traffic, growth potential, compliance
risk). The weights weren't hand-picked: grid search inside business-informed bounds, validated with
Spearman rank consistency to confirm the tiers were stable. Also a churn model over **80k+
behavioural records**, built on trend features like period-over-period change, with strictly
time-ordered train/validation splits to avoid leakage.

---

## Tools

`Python` (pandas, scikit-learn, PyTorch) for modeling · `SQL` for everything upstream of it ·
`Power BI` / `Tableau` when the audience won't run a notebook · `Git` / `GitHub Actions`

Chinese (native) · English (fluent) · Japanese (JLPT N2)

---

## 中文

卡内基梅隆大学信息系统管理硕士（商业智能与数据分析方向），2026 年 12 月毕业。本科是上海外国语大学
国际经济与贸易（日语）。

我的工作大多落在"模型"和"决策"之间：把一条复杂的激励规则翻译成可核验的脚本、把策略影响从活动本身的
自然衰减里剥离出来、把三十个口径打架的数据源统一到一个定义上，或者在并不完全可信的预测之上决定五台
发电机放哪里。这段中间地带是我最感兴趣的部分。

置顶的 [停电预测与发电机投放](https://github.com/wangruig-lang/MLPS_Final_Project) 是最能代表我的项目：
24h RMSE 92.17，比历史均值基线低 18.8%；发电机方案缓解 66.4% 的停电量，比"按人口投放"的常规做法高
15 个百分点。但更值得看的是里面记录的三件事——我花了三天调 LSTM 的损失函数，最后发现同样特征下梯度提升
四秒钟就赢了 37 个 RMSE 点；一个看起来像过拟合的现象其实是验证集划分导致的分布错配；以及发电机方案有一个
我主动写进 README 的失效场景（风暴中心位置预测错，方案几乎完全失效）。

实习方面：在 **字节跳动 TikTok LIVE** 做商业分析实习生，支持日本、韩国、台湾三地的公会与主播运营。
banner 精准推流策略推全后曝光下降、团队一度考虑回滚，我负责曝光归因：拆出单独的页面展示缺陷交给技术修复，
再按周、双周、头部活动三个粒度重切数据，定位为头部活动的生命周期衰减，团队据此保留策略；落地台湾 Q3
拉新激励的核验脚本（框架由 leader 与业务同学确定，申报覆盖率 40% → 70%）；治理一次周报倒挂的口径问题；
把人工日查改造成定时刷新的托管看板（三地每周省约 6 小时），并做了活动信息催办机器人（日均 150 条，
及时率 60% → 90%）。在 **均胜安全**（上海）统一 30 个数据源口径，覆盖 200 多条产线搭建 100 多项指标的
异常监控；在 **京东物流**（北京）做商家四维分层（权重用网格搜索 + 斯皮尔曼一致性验证）与 8 万条行为数据的
流失预测。

另有 AI 能力测评项目（双语六维，我负责题库治理与大模型评分一致性：三个互盲的大模型评分者一致率从 57%
提升到 68%），以及 11-785 深度学习课程作业（音素分类、ArcFace 人脸分类与验证、CTC 与 attention 两套
语音识别）——五次 Kaggle 课程竞赛**均进入前 10%，课程成绩 A+**。两者因涉及团队授权与课程作业，仓库均未公开。
