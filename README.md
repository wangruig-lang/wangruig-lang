# Wangrui Gong · 龚王睿

MS in Information Systems Management (Business Intelligence & Data Analytics) at **Carnegie Mellon**,
graduating December 2026. Before that, International Economics & Trade — studied in Japanese — at
Shanghai International Studies University.

Most of what I do sits between a model and a decision. Encoding a messy incentive rule into
something checkable, separating a strategy's effect from a campaign's natural decay, getting thirty
disagreeing data sources onto one definition, or deciding where five generators go given a forecast
you don't fully trust — that middle part is the work I like.

📮 gongwangrui@gmail.com · Pittsburgh, PA

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
A faculty-advised, CMU-incubated project; six of us. I designed the six-dimension capability
taxonomy, the bilingual item bank and the assessment flow, and built the internal review workbench
(try-it / browse / dashboard modes, per-module annotation, dimension and difficulty re-checks).
The hard problem is **LLM grading consistency**: the same free-response answer scores differently
across runs. Tightening rubrics and adding blind double-review brought the variance down, and
scattered tester feedback became tracked revision tasks so recurring issues hardened into reusable
review rules.

**Deep learning coursework** *(private — CMU 11-785)*
Frame-level phoneme classification, face recognition and verification with ArcFace, and two speech
recognition systems (CTC and attention-based) — **top 10% on all four Kaggle leaderboards, A+ in the
course**. Repos stay private: they're graded assignments with reference solutions.

---

## Experience

**ByteDance · TikTok LIVE** — Product & Data Operations Intern · Jun–Aug 2026
Guild and creator operations for Taiwan, supporting Japan and Korea.

- Encoded a four-condition eligibility rule (first-time membership, sub-$30 prior monthly revenue,
  a 15-day cooling-off window, a 7-day trial exemption) into a verification script that reconciled
  200+ applicants against six months of full-population records, catching both under-reporting and
  ineligible claims. Application coverage went **40% → 70%** and held.
- A new incentive shipped, campaign-page impressions fell across all three markets, and the team
  was split on rolling back. I separated the campaign's own lifecycle decay from the strategy's
  effect — RCT results cross-checked against how comparable campaigns behaved before and after —
  and showed engagement and revenue were intact. **The rollback was called off**, and a top-campaign
  exemption mechanism landed.
- Rebuilt the high-value-guild dashboard from a query someone ran by hand every day into a scheduled
  page with fallback validation, so ops in three markets could self-serve (**~6 hours/week** back).
  A companion bot chases incomplete campaign records — field validation, owner outreach, status
  write-back — at **150 records/day**, lifting completeness **60% → 90%**.

**Joyson Safety Systems** — Data Analyst Intern · Feb–May 2024
Production-line monitoring. The real problem wasn't modeling, it was that **30 data sources** —
SQL, Excel ledgers, line systems — disagreed on field definitions, product codes and time
granularity, so planned-vs-actual variance couldn't be computed at all. I reconciled them onto one
base (shift / day / week), then built anomaly detection over **100+ metrics** across **200+
production lines**: historical baseline, normal-variation band and a persistence test, with
seasonal threshold correction and a consecutive-breach rule to keep false alarms down. Drill-down
by line, time window and product means an alert points at a cause, not just a number.

**JD Logistics** — Data Analyst Intern · Jul–Aug 2023
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

实习方面：在 **字节跳动 TikTok LIVE** 负责台湾市场公会与主播运营并协同日韩，把四类判断条件的激励
核验脚本化（申报覆盖率 40% → 70%）、用随机对照实验结果剥离活动生命周期衰减从而支撑团队决定不回滚、
把人工日查改造成托管看板（三地每周省约 6 小时）并做了活动信息催办机器人（日均 150 条，及时率
60% → 90%）；在 **均胜安全** 统一 30 个数据源口径，覆盖 200 多条产线搭建 100 多项指标的异常监控；
在 **京东物流** 做商家四维分层（权重用网格搜索 + 斯皮尔曼一致性验证）与 8 万条行为数据的流失预测。

另有 AI 能力测评项目（双语六维，负责题库治理与大模型评分一致性），以及 11-785 深度学习课程作业（音素分类、
ArcFace 人脸识别、CTC 与 attention 两套语音识别）——四次 Kaggle 竞赛**均进入前 10%，课程成绩 A+**。
两者因涉及团队授权与课程作业，仓库均未公开。
