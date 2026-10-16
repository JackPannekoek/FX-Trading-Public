FXD ADAPTIVE EA RESEARCH – FULL RECOVERY CONTEXT

Do not reinterpret or redesign the project from scratch simply because you are a newer model. Treat this file as accumulated research state and standing project governance. Improve the work prospectively, but preserve prior decisions unless new test evidence justifies changing them.

Use the latest actual MQ4 and logs as authoritative over the transfer summary whenever there is any conflict.

Recovery point: after v2p60 test results
Purpose: paste this entire file into a new ChatGPT conversation so the EA research can resume from the current accumulated design logic, governance rules, version history, and next-step decisions.

============================================================
1. PRIMARY RESEARCH OBJECTIVE
============================================================
Develop an adaptive FX Expert Advisor (MT4, H1 EURUSD baseline) that:

1) Recognizes changes in current market behavior from candle/statistical information.
2) Selects or prioritizes the sub-EA algorithm(s) best suited to the current behavior.
3) Preserves multiple sub-EAs with different specialties rather than assuming one algorithm works everywhere.
4) Keeps sidelined algorithms under lightweight virtual/shadow evaluation so they can become relevant again when market behavior changes.
5) Continues algorithm discovery when the current roster is collectively inadequate.
6) Avoids calendar/data fitting and instead derives regime/behavior decisions from live-observable candle statistics.
7) Ultimately targets high CAGR, with an aspirational target of approximately 6% monthly compounded / doubling in about 12 months, while controlling drawdown and preserving sufficient trade cadence.

The two central technical problems are:
A. Correctly describing/recognizing current market behavior.
B. Correctly adapting participation and sub-EA selection to that behavior.

Sub-EAs are of limited value without a robust behavior recognition/router layer.

============================================================
2. CURRENT TEST SCOPE / DATA / PLATFORM
============================================================
Primary platform: MT4 / MQL4.
Primary baseline pair/timeframe: EURUSD H1.
Current development test window: 2010–2019 unless otherwise instructed.
Current tester characteristics frequently used:
- Bars: 62,932
- Modelling quality: 90.00%
- Spread: 10
- Initial deposit: 10,000
- 6 mismatched chart errors commonly appear in this dataset/test setup.

There was an earlier branch focused specifically on 2015–2019 because later years were difficult, but the current adaptive-router branch has returned to the 2010–2019 test window.

Do not data-fit by calendar segment. Behavior descriptions and region/state recognition must come from candle statistics, not date ranges or trade-result history.

============================================================
3. FILE NAMING / VERSIONING / BUILD RULES
============================================================
EA source filenames must remain simple:
FXD_AdaptiveEA_v2pNN.mq4

SET filenames:
FXD_AdaptiveEA_v2pNN_2010_2019_DEV.set

Do NOT append descriptors such as _fixed, _router, _behavior, etc. to the filename.
Descriptive branch text belongs in the source code top comment/banner only.

RunTag must always match the current version exactly, e.g.:
ADAPTIVE_EA_V2P60_2010_2019_DEV

When fixing compile errors, repair the same version in place. Do not increment the version merely for a compile repair.

Log filenames are versionless and overwrite each run rather than append.
Typical files:
FXD_AdaptiveEA_StateLog_<Symbol>_<Period>.csv
FXD_AdaptiveEA_TradeLog_<Symbol>_<Period>.csv
FXD_AdaptiveEA_AlgoSummary_<Symbol>_<Period>.csv

Do not repeatedly warn that MT4 compilation cannot be checked here. User supplies compiler errors if any.

============================================================
4. DEVELOPMENT GOVERNANCE / WORKING STYLE
============================================================
Primary evaluation focus is not merely aggregate EA PF. The project tracks the usefulness and market-behavior relevance of each sub-EA.

Key reporting metrics:
- CAGR (main long-term objective)
- Profit Factor (PF)
- Max drawdown
- Trade cadence / trades per day
- Net profit
- Win rate
- Average win / loss
- Per-sub-EA attributed CAGR
- MaxDD contribution
- WorstTradeDDImpact
- AvgLossDDImpact
- AvgDDImpactPerTrade
- State/behavior-specific PnL where possible

Algorithm summary tables should mark algorithm outcomes:
🟢 improved / positive evidence
🟡 little difference / mixed / inconclusive
🔴 failed / materially negative

Failure workflow:
- Diagnose why a test failed.
- Research/consider known remedies.
- Replace algorithms when necessary instead of endlessly tuning a failed concept.
- Multiple sub-EA changes in one version are permitted when justified.
- Attribution by sub-EA is critical.

Entry logic should be framed affirmatively: the EA should want to open trades when evidence supports them, not merely consist of layers of “blocking” rules.

============================================================
5. SUB-EA PROBATION / REPLACEMENT RULES
============================================================
New sub-EA algorithms generally require optimization before fair judgment.
Standing rule:
- Keep a newly introduced sub-EA for a minimum of roughly 3–6 adjustment passes before discarding it.
- Early discard is acceptable only if it is clearly catastrophic and repeatedly harmful with no sign of useful behavior specialization.

When dropping a sub-EA:
- Keep it tracked/sidelined rather than deleting it permanently.
- Introduce 1–2 new candidate sub-EAs when a truly failed algorithm is dropped, unless a sidelined algorithm has enough current profitability promise to deserve reactivation first.

Replacement priority historically considered lowest number of successful results / weakest accumulated evidence, but the newer relevance/profitability architecture now provides a better replacement mechanism.

============================================================
6. PF 1.10 ALGORITHM-DISCOVERY RULE
============================================================
Standing governance rule:

If overall EA Profit Factor < 1.10:
- Assume the current roster may be inadequate.
- Continue considering new sub-EA algorithms until there is a credible path to PF >= 1.10.

CAVEAT / FIRST-RIGHT-OF-RETURN RULE:
If PF < 1.10 BUT a passive/sidelined sub-EA shows sufficiently strong Profitability Promise/Potential and evidence that reactivation could plausibly lift aggregate PF back above 1.10:
- Prioritize evaluating/reactivating that passive sub-EA before inventing a new algorithm.

If PF < 1.10 and no sidelined sub-EA has sufficient profitability promise:
- Introduce genuinely new sub-EA candidates.

PF 1.10 is not the final target or “mission accomplished.” It is the minimum threshold at which mandatory algorithm discovery can pause and attention can shift more toward robustness, CAGR, routing quality, DD, etc.

============================================================
7. CURRENT SUB-EA ROSTER / HISTORY
============================================================
Algorithms used through this development line have included:
- Breakout
- Pullback
- CompressionRelease
- ShortHold
- DriftContinuation (later repurposed)
- ReversalConfirmation (later replaced)
- RangeReclaim
- DelayedConfirmation
- TrendRetest

Important historical transitions:
- Breakout became a chronic drag and was eventually replaced by TrendRetest.
- DriftContinuation/ReversalConfirmation was replaced by RangeReclaim.
- CompressionRelease and ShortHold were sidelined at points but retained for future relevance.
- DelayedConfirmation moved between probation and sidelined status.
- Pullback was eventually sidelined after becoming a dominant loss source, while still being shadow-evaluated.

Current architecture around v2p60 includes:
LIVE/PROBATION candidates:
- TrendRetest
- CompressionRelease
- RangeReclaim
- DelayedConfirmation (reactivated in prior pass, but v2p60 live test showed this reactivation failed badly and it should return to sidelined status next)

SIDELINED / SHADOW EVALUATED:
- Pullback
- ShortHold

Recommended immediate roster action after v2p60:
- DelayedConfirmation -> SIDELINED again.
- Pullback is the strongest current sidelined comeback candidate by readiness/promise metrics and deserves controlled probation re-entry before inventing a new algorithm.
- RangeReclaim remains the strongest current live/probation algorithm.
- CompressionRelease stays under probation.
- TrendRetest stays under probation but needs further meaningful refinement due regression in v2p60.
- ShortHold remains sidelined/shadow evaluated.

============================================================
8. BEHAVIOR-DETECTION / ROUTER ARCHITECTURE
============================================================
Critical principle:
Sub-EA selection must be driven by CURRENT MARKET BEHAVIOR, not recent trade PnL.

The architecture evolved from coarse categorical states toward a richer continuous descriptor model.

Old/coarse behavior/state labels include:
- UNKNOWN
- TRANSITION
- LongBiasDirectional
- ShortBiasDirectional
- BalancedExpansion
- LowVolCompression
- ShockExpansion

These state names are now treated as useful summaries/weak priors rather than the sole routing basis because they proved too coarse.

Continuous behavior descriptors introduced around v2p56 include concepts such as:
- persistence
- directional agreement
- expansion
- compression
- noise/choppiness
- structural stability
- path efficiency
- overlap
- follow-through
- breakout asymmetry
- volatility state
- long/short asymmetry

Desired routing flow:
Candle/statistical features
 -> behavior descriptor profile
 -> behavior confidence
 -> eligible sub-EAs
 -> descriptor-fit ranking among eligible algorithms
 -> selected specialist / trade intent

Router confidence classes:
- LOW
- MEDIUM
- HIGH

Low-confidence environments should not force an arbitrary specialist. UNKNOWN/TRANSITION can be used when evidence is weak or conflicting.

Behavior confidence should reflect how strongly the current statistics support a particular description, including the distinctiveness of the current descriptor profile.

The router should log enough information to validate itself, including fields such as:
- detected behavior/state
- RouterConfidenceLong / Short
- RouterClassLong / Short
- EligibleAlgosLong / Short
- RouterSelectedLong / Short
- RouterMarginLong / Short
- DescriptorPersistenceLong / Short
- DescriptorExpansion
- DescriptorCompression
- DescriptorNoise
- DescriptorStability

Key architectural objective:
The EA must be able to answer on each decision cycle:
“What is the market doing now, how confident am I in that description, and which sub-EA is currently best suited to it?”

============================================================
9. IMPORTANT BEHAVIOR-SPECIALTY EVIDENCE FOUND SO FAR
============================================================
These relationships are empirical clues from recent runs, not permanent hard-coded truths. Continue validating them against continuous descriptors and new runs.

RangeReclaim:
- Repeatedly strongest or near break-even among current live algorithms.
- Often useful in non-directional/change-of-state environments.
- Recent positive examples have included TRANSITION, ShockExpansion, BalancedExpansion.
- Established directional states have repeatedly been its weakness.
- v2p60 state split included approximately:
  - ShockExpansion +137.44
  - Transition +141.09
  - BalancedExpansion +21.60
  - directional states remain weak.

TrendRetest:
- Repeated evidence as a ShockExpansion specialist.
- Had runs where ShockExpansion was clearly positive while directional/Transition participation caused losses.
- v2p60 overall regressed, so specialty still needs controlled refinement.

CompressionRelease:
- Has repeatedly shown some useful Transition behavior in certain runs.
- Has also failed badly when allowed to dominate the overall trade stream.
- Do not allow one sub-EA to capture most trades merely because it wins a broad score competition.

Pullback:
- Was a dominant active drag in several runs.
- Subsequently sidelined and shadow-evaluated.
- v2p60 passive/shadow metrics showed meaningful comeback promise (see section 13).

DelayedConfirmation:
- Historically inconsistent.
- Was sidelined, then ranked highly during shadow evaluation and was reactivated.
- v2p60 live reactivation failed badly, demonstrating that relevance/promise must be validated live before trust.
- Should return to sidelined status after v2p60.

ShortHold:
- Sidelined.
- Small shadow samples have sometimes shown attractive win rates, but evidence is much thinner than Pullback.

============================================================
10. LIVE VS SIDELINED ALGORITHM ARCHITECTURE
============================================================
A sidelined sub-EA must be:
- completely ineligible for live routing/trading;
- impossible to select as a live fallback;
- still evaluated in a lightweight virtual/shadow manner.

This was introduced because future market conditions may make a currently irrelevant sub-EA relevant again.

Important implementation concept: TWO-SPEED EVALUATION.

A) Cheap continuous descriptor relevance:
- Every sidelined sub-EA receives a low-cost relevance score from the current behavior descriptor profile.

B) Sparse shadow effectiveness probes:
- Only when a sidelined algorithm sees a sufficiently strong hypothetical setup does it open a lightweight virtual/shadow probe.
- At most one active shadow probe per sidelined sub-EA.
- Shadow probe has a defined evaluation horizon (v2p58 used six bars).
- No real MT4 trade is opened.

Goal: preserve dormant algorithm awareness without making every sidelined algorithm run a full parallel virtual trading engine on every tick.

============================================================
11. DORMANT / SIDELINED ALGORITHM METRICS
============================================================
The dormant-roster architecture now distinguishes several concepts.

RelevanceFactor:
- “How closely does the current market resemble the environment this algorithm is designed for?”
- It is NOT the same as profitability.

DescriptorRelevance:
- raw descriptor-fit component.

ShadowTrades:
- number of virtual/shadow probes evaluated.

ShadowWins / ShadowWinRatePct:
- shadow effectiveness statistics.

ShadowNetR:
- aggregate shadow outcome in R units.

ProfitabilityPotential (also referred to conversationally as Profitability Promise):
- “Given recent shadow outcomes, relevance, and evidence quality, how plausible is profitable reactivation?”
- Designed to incorporate relevance + shadow expectancy + shadow win rate + sample-size confidence.

RelevancePersistence:
- measures how consistently relevance remains materially high rather than briefly spiking.

ReplacementReadiness:
- conservative composite intended to combine ProfitabilityPotential, current relevance, relevance persistence, and shadow evidence confidence.

Ranks:
- ReactivationRank: ranked primarily by current relevance.
- ReplacementRank: ranked primarily by ProfitabilityPotential.
- ReadinessRank: ranked by the more conservative ReplacementReadiness composite.

Important principle:
Do NOT collapse “relevance” and “profitability” into one concept too early.
An algorithm can be highly relevant but still unprofitable.

============================================================
12. ADAPTIVE ROSTER CYCLE
============================================================
Desired long-term lifecycle:

1) Active/probation sub-EA performs poorly or loses relevance.
2) It is sidelined, not deleted.
3) While sidelined, descriptor relevance and shadow effectiveness continue to be measured.
4) Current passive roster is ranked by Relevance, ProfitabilityPotential, Persistence, and Readiness.
5) When a live slot needs replacement:
   a) first inspect sidelined algorithms with strong Profitability Promise/Readiness;
   b) if one has credible evidence, reactivate it into probation;
   c) if none does and aggregate PF < 1.10, introduce a genuinely new sub-EA algorithm.
6) Any reactivated or new candidate gets a proper probation/evaluation runway.
7) Algorithms can cycle between active/probation/sidelined as market behavior evolves.

This is intended to make the EA “alive” and adaptive while containing computational overhead.

============================================================
13. MOST RECENT TEST RESULT – v2p60
============================================================
Latest supplied tester result:

Bars in test: 62932
Ticks modelled: 163639195
Modelling quality: 90.00%
Mismatched chart errors: 6
Initial deposit: 10000.00
Spread: 10
Total net profit: -2532.45
Gross profit: 21913.07
Gross loss: -24445.52
Profit factor: 0.90
Expected payoff: -0.79
Absolute drawdown: 2534.32
Maximal drawdown: 2990.98 (28.60%)
Relative drawdown: 28.60%
Total trades: 3197
Short won: 42.25%
Long won: 40.44%
Overall win rate: 41.41%
Largest profit trade: 86.00
Largest loss trade: -66.08
Average profit trade: 16.55
Average loss trade: -13.05

Recent comparison:
- v2p58: net -3036.02, PF 0.88, DD 34.10%, 3277 trades.
- v2p60: net -2532.45, PF 0.90, DD 28.60%, 3197 trades.
Thus v2p60 materially improved net loss and drawdown, but PF remains far below 1.10.

v2p60 sub-EA summary interpreted from the uploaded algo summary:
- TrendRetest: 820 trades, 41.46% wins, net -756.94, MaxDD 1026.94, AvgDD/trade 7.91. Regressed.
- CompressionRelease: 905 trades, 43.31% wins, net -289.51, MaxDD 812.26, AvgDD/trade 8.01. Improved materially.
- RangeReclaim: 617 trades, 43.60% wins, net -32.19, MaxDD 385.01, AvgDD/trade 6.09. Best live sub-EA, essentially break-even.
- DelayedConfirmation: 855 trades, 37.43% wins, net -1453.81, MaxDD 1612.28, AvgDD/trade 8.13. Reactivation failed badly; return to sidelined.
- Pullback: sidelined, zero live trades, shadow-evaluated.
- ShortHold: sidelined, zero live trades, shadow-evaluated.

v2p60 dormant metrics:
Pullback:
- RelevanceFactor: 0.5811
- ShadowTrades: 625
- ShadowWinRate: 48.96%
- ShadowNetR: +18.671R
- ProfitabilityPotential: 0.5826
- RelevancePersistence: 0.0291
- ReplacementReadiness: 0.5133
- ReadinessRank: #1

ShortHold:
- RelevanceFactor: 0.4810
- ShadowTrades: 42
- ShadowWinRate: 59.52%
- ShadowNetR: +4.805R
- ProfitabilityPotential: 0.5244
- RelevancePersistence: 0.0106
- ReplacementReadiness: 0.4087
- ReadinessRank: #2

Interpretation:
- Pullback currently has enough passive evidence to justify a controlled comeback test before inventing another new algorithm.
- ShortHold is promising but sample size is much smaller.
- DelayedConfirmation’s previous shadow promise did not survive live reactivation, so live validation is mandatory.

============================================================
14. RECENT VERSION HISTORY / KEY LESSONS
============================================================
v2p47:
- Breakout, Pullback, ReversalConfirmation, DelayedConfirmation all negative.
- ReversalConfirmation lowest successful result count and replaced.

v2p48:
- Introduced RangeReclaim in former Drift/Reversal slot.
- RangeReclaim was best new probation candidate by DD-quality metrics.

v2p49–v2p51:
- Several routing/selection adjustments mostly failed or regressed.
- Established that repeated tiny tweaks were not enough.

v2p52:
- Replaced broad Breakout with TrendRetest.
- Whole EA materially improved versus v2p51: net around -4230, DD 44.19%.
- RangeReclaim improved strongly.

v2p53:
- Shifted toward evidence-based behavior specialization.
- Net improved to about -3470.73, DD 39.80%.
- Found behavior-specific differences:
  RangeReclaim profitable in some BalancedExpansion conditions;
  CompressionRelease sometimes useful in ShortBiasDirectional/Transition depending run;
  TrendRetest initially weak overall.

v2p54:
- More explicit behavior specialization.
- Net -3325.26, DD 38.81%.
- CompressionRelease accidentally dominated ~77% of trades and lost heavily.
- Demonstrated need for an explicit behavior router rather than free score competition.

v2p55 – Behavior Router v1:
- Explicit behavior -> confidence -> eligible algorithms -> selected specialist routing.
- Net -3339.50, PF 0.87, DD 38.89%, 3274 trades.
- Router worked technically but behavior descriptions/confidence were too weak/coarse.
- Transition was a problematic residual bucket.

v2p56 – Behavior Descriptor v2:
- Added richer continuous descriptor profile and confidence classes.
- Net improved to -2563.75, PF 0.90, DD 29.60%, 3307 trades.
- Improvement did not come merely from reducing trade count.
- TrendRetest nearly break-even overall and strong in ShockExpansion.
- Continuous descriptors appeared more informative than coarse labels.

v2p57 – Router validation/refinement:
- Improved HIGH confidence distribution but overall net regressed to -2736.40, DD 30.80%.
- RangeReclaim close to break-even; useful in non-directional/change-of-state environments.
- Pullback became obvious largest drag.
- Discovered a critical implementation leak: sidelined DelayedConfirmation still traded live.

v2p58:
- Fixed sidelined enforcement so sidelined means zero live trades by construction.
- Added lightweight relevance + shadow evaluation for sidelined algorithms.
- Net -3036.02, PF 0.88, DD 34.10%.
- DelayedConfirmation and ShortHold had zero live trades but useful shadow metrics.
- DelayedConfirmation ranked #1 then; ShortHold #2.
- RangeReclaim remained best live algorithm.
- Pullback was identified as the major live drag and candidate for sidelining.

v2p59:
- Added ProfitabilityPotential and ReplacementRank.
- Pullback moved to sidelined/shadow evaluation.
- DelayedConfirmation reactivated to probation based on prior dormant promise.
- User later moved directly to v2p60 without providing a separate v2p59 result.

v2p60:
- Added RelevancePersistence, ReplacementReadiness, ReadinessRank.
- Roster unchanged from v2p59 for a clean architectural step.
- Test result improved aggregate loss/DD, but DelayedConfirmation live reactivation failed badly.
- Pullback now has strongest passive ReadinessRank and profitability promise.

============================================================
15. CURRENT NEXT-STEP DECISION LOGIC
============================================================
At recovery point after v2p60:

Aggregate PF = 0.90, below mandatory-discovery threshold of 1.10.
However, the caveat applies because Pullback currently has substantial passive Profitability Promise / Replacement Readiness.

Therefore immediate next version should NOT yet invent a new sub-EA.

Recommended next roster action:
1) DelayedConfirmation -> SIDELINED again because its live reactivation failed badly.
2) Pullback -> controlled PROBATION re-entry because it is the highest-readiness sidelined algorithm:
   - 625 shadow trades
   - +18.671R shadow outcome
   - ProfitabilityPotential 0.5826
   - ReadinessRank #1
3) ShortHold stays sidelined/shadow evaluated.
4) RangeReclaim remains live/probation and should be protected from clearly bad directional descriptor environments.
5) CompressionRelease remains probation.
6) TrendRetest remains probation but needs a meaningful refinement consistent with its remaining useful behavior specialty evidence, especially ShockExpansion.
7) Keep behavior-descriptor/router architecture and confidence calibration; do not revert to broad score competition.
8) Keep all dormant metrics and ranks active.

Decision after that controlled Pullback re-entry test:
- If Pullback reactivation materially improves PF/net/DD and shows a valid behavior specialty, keep refining it within probation.
- If Pullback reactivation fails AND overall PF remains < 1.10, then the passive-roster exception has failed and a genuinely NEW sub-EA algorithm must be introduced.
- New candidate must then receive the normal 3–6 adjustment passes unless catastrophic.

============================================================
16. WHAT A “NEW SUB-EA” SHOULD MEAN
============================================================
Do not merely rename an old algorithm or tweak thresholds and call it new.
A new sub-EA should have a materially different trade thesis / market-behavior hypothesis.

Examples of distinct theses historically used:
- breakout continuation
- pullback
- compression-release
- short-hold
- drift continuation
- reversal confirmation
- range reclaim
- delayed confirmation
- trend retest

When introducing future algorithms, explicitly state:
- intended market behavior
- affirmative entry thesis
- descriptor conditions it should prefer
- conditions it should avoid
- expected trade management characteristics
- probation pass number
- how its contribution will be attributed and evaluated.

============================================================
17. RISK / USER-FACING SETTINGS
============================================================
RiskComfort is a user-facing integer scale 1–5.
It should meaningfully influence internal trade decisions/risk behavior rather than being cosmetic.

SET files should accompany each test version.
Only generate a new MQ4 when logic changes; parameter-only changes can use a new SET if appropriate, although recent architecture work has generally changed code.

Trade management should often remain unchanged across router/descriptor experiments when attribution requires isolating routing effects.

============================================================
18. LOGGING / REPORTING EXPECTATIONS
============================================================
Maintain one CSV per log type; overwrite rather than append.
Versionless log filenames.
RunTag records actual version.

When analyzing a test:
1) Identify RunTag/version first so duplicate reruns are not mistaken for new evidence.
2) Report compact overall metrics.
3) Prioritize sub-EA table and attribution.
4) Analyze behavior/state or descriptor specialization where logs support it.
5) Do not invent feature/entry conclusions not present in logs.
6) Explicitly investigate positive -> negative flips rather than dismissing them.
7) Evaluate dormant algorithms using relevance + profitability + persistence + sample confidence.
8) Keep aggregate PF/CAGR important but do not let them obscure which algorithms work in which behaviors.

The user sometimes takes breaks between builds and may accidentally rerun an older build. Treat RunTag and uploaded AlgoSummary as source of truth. If a result duplicates an older run, identify it calmly and do not over-analyze it as new evidence.

============================================================
19. ARCHITECTURAL PRINCIPLES TO PRESERVE
============================================================
- Behavior-first, not trade-result-first adaptation.
- Known / transition / unknown concepts remain useful.
- Allow UNKNOWN or low-confidence state rather than forcing a label.
- Continuous descriptors should be more important than coarse categorical labels.
- No fixed calendar regime switching.
- Preserve virtual/shadow evaluation.
- Preserve adaptive layer as a separable/toggleable architectural concept where practical.
- Avoid data fitting.
- Maintain enough trade cadence for compounding; historically 1 trade/day was considered acceptable, with earlier desire for roughly 10–20% time-in-market.
- Focus on high CAGR but preserve capital in adverse regimes.
- Do not optimize only the front half of the dataset; the later/back part has historically been harder and should remain an explicit robustness concern.
- Final architecture should scale to many behavior regions/states (eventually 100+ if needed) without relying on manually hard-coded date regions.

============================================================
20. USER EXPECTATIONS / INTERACTION STYLE FOR THIS PROJECT
============================================================
The user wants:
- fast iteration to the next version after results are supplied;
- compact but rigorous sub-EA-first analysis;
- real algorithmic changes when tweaks repeatedly fail;
- proactive reasoning about why changes failed;
- new candidate algorithms when the roster is insufficient;
- sidelined algorithms retained and monitored for future relevance;
- explicit version/run-tag discipline;
- rich in-code comments explaining design intent, branch purpose, and findings;
- no unnecessary repetition of already-known limitations;
- no “blocking” framing for entries; describe positive trade intent and suitability instead.

============================================================
21. RECOVERY INSTRUCTION TO A NEW CHAT
============================================================
If this file is pasted into a new chat, treat it as authoritative project context and resume from the recovery point after v2p60.

First immediate task should be to confirm the current next version number and create the next test build unless the user asks for analysis instead.

The next version after this recovery point should normally:
- sideline DelayedConfirmation again;
- reactivate Pullback into controlled probation based on its current shadow Profitability Promise / ReadinessRank;
- preserve RangeReclaim, CompressionRelease, TrendRetest under their current probation/development logic;
- preserve ShortHold as sidelined/shadow-evaluated;
- preserve the Behavior Descriptor / Router architecture;
- preserve RelevanceFactor, ProfitabilityPotential, RelevancePersistence, ReplacementReadiness, ReactivationRank, ReplacementRank, ReadinessRank;
- keep PF<1.10 algorithm-discovery rule active;
- defer genuinely new algorithm introduction for this one controlled Pullback re-entry test because Pullback currently satisfies the passive-candidate caveat;
- if that comeback test fails and PF remains <1.10, introduce a genuinely new sub-EA candidate next.

END OF RECOVERY CONTEXT


===================================================================
ADDENDUM — AUTHORITATIVE UPDATES AFTER v2p60
===================================================================

This addendum supersedes any conflicting material above and brings the recovery context fully current through the creation of v2p64.

CURRENT PROJECT POINT
---------------------
- Latest CREATED EA: FXD_AdaptiveEA_v2p64.mq4
- Latest TESTED EA: v2p63
- v2p64 has been created but has NOT yet been tested.
- Primary pair/timeframe remains EURUSD H1.
- Standing focus remains behavior recognition, specialist routing, dormant-sub-EA evaluation, and algorithm discovery while PF remains below 1.10.

PERMANENT PF / DISCOVERY RULE
-----------------------------
Overall PF < 1.10 normally triggers continued search for new sub-EA algorithms.

Caveat:
If PF < 1.10 but a passive/sidelined sub-EA has sufficiently strong Profitability Promise / Profitability Potential and Replacement Readiness to plausibly raise aggregate PF above 1.10, evaluate/reactivate that passive candidate BEFORE inventing a new algorithm.

If that reactivation fails live, the passive-candidate exception is considered tested/exhausted for that cycle and new algorithm discovery resumes if PF remains below 1.10.

PF >= 1.10 removes the mandatory discovery trigger, but does NOT mean the EA is finished.

NEW-SUB-EA PROBATION RULE
-------------------------
Every genuinely new sub-EA should normally receive 3–6 adjustment passes before being discarded, unless there is an obvious catastrophic/structural failure.

Reason:
A new algorithm often needs some optimization/refinement before a fair decision can be made.

DORMANT / SIDELINED SUB-EA ARCHITECTURE
---------------------------------------
A sidelined sub-EA must:
- have zero live-trade eligibility
- never become a live fallback
- still be evaluated continuously enough to detect renewed usefulness under changing market behavior

The intended low-overhead two-speed design is:
1. Cheap descriptor relevance each bar.
2. Sparse shadow/virtual probes only when a sidelined algorithm's descriptor fit is strong enough.

Dormant metrics now include or should continue to include:
- RelevanceFactor
- DescriptorRelevance
- ShadowTrades
- ShadowWins
- ShadowWinRatePct
- ShadowNetR
- ProfitabilityPotential
- RelevancePersistence
- ReplacementReadiness
- ReactivationRank
- ReplacementRank
- ReadinessRank
- ReactivationCooldownPenalty

Interpretation:
RelevanceFactor = how much the current market resembles the environment the algorithm was designed for.
ProfitabilityPotential = how plausible profitable reactivation looks from relevance + shadow outcomes + evidence quality.
ReplacementReadiness = conservative reactivation measure incorporating potential, relevance, persistence, sample confidence, and cooldown/history.

A recently failed live reactivation should receive a cooldown/history penalty so the same algorithm cannot immediately cycle back to the top merely because its shadow metrics rebound.

BEHAVIOR ROUTER — PERMANENT ARCHITECTURAL PRINCIPLE
---------------------------------------------------
Specialized sub-EAs are only useful if the EA can suitably detect/describe the current market behavior and load/select the best-suited sub-EA.

The router should prioritize continuous market descriptors over coarse category labels.
Useful descriptors include:
- persistence
- directional agreement
- expansion
- compression
- noise/choppiness
- structural stability
- path efficiency
- overlap
- breakout/follow-through characteristics
- directional asymmetry/context

Coarse state labels may still include:
- TRANSITION
- LongBiasDirectional
- ShortBiasDirectional
- BalancedExpansion
- ShockExpansion
- LowVolCompression
- UNKNOWN

These labels are context summaries, not sufficiently rich primary routing signals by themselves.

Router confidence classes:
- LOW
- MEDIUM
- HIGH

The router should be allowed to remain uncertain instead of forcing a specialist when evidence is weak or candidate margins are too small.

IMPORTANT LATE-BRANCH VERSION RESULTS
-------------------------------------
v2p61 — Controlled Pullback reactivation
Overall:
- Net -1751.42
- PF 0.93
- MaxDD 21.50%
- Trades 3298

Pullback reactivation failed:
- 239 trades
- 38.08% win
- Net -323.99

This demonstrated that strong dormant/shadow promise does not necessarily survive live reactivation.

RangeReclaim remained strongest live candidate at that stage:
- 934 trades
- Net -76.85
- positive mainly in Transition / ShockExpansion / BalancedExpansion
- negative in established directional states

v2p62 — Two new discovery-cycle algorithms introduced
Overall:
- Net -2165.39
- PF 0.91
- MaxDD 24.69%
- Trades 3317

MomentumContinuation — probation pass 1:
- 301 trades
- 39.87% win
- Net -334.16
- positive ShortBiasDirectional pocket

ExhaustionReset — probation pass 1:
- 245 trades
- 45.31% win
- Net +51.53
- first new algorithm in this discovery cycle to finish a full pass profitable
- positive LongBiasDirectional / ShockExpansion pockets
- Transition negative

v2p63 — Pass 2 for new algorithms
Overall:
- Net -1429.44
- PF 0.93
- MaxDD 16.42%
- Trades 2614

This is the BEST TESTED RESULT in the current branch at the time of this transfer.

MomentumContinuation — pass 2:
- 52 trades
- 50.00% win
- Net +170.81
- ShortBiasDirectional: 38 trades, +178.92
- emerging identity: clean ShortBiasDirectional continuation specialist

ExhaustionReset — pass 2:
- 128 trades
- 51.56% win
- Net +318.96
- strongest new algorithm so far
- emerging identity: late-directional / shock-exhaustion / reset specialist

CompressionRelease in v2p63:
- 1475 trades
- Net -1270.39
- negative across states
- became obvious sideline candidate

TrendRetest in v2p63:
- 212 trades
- Net -401.95
- 36.32% win
- former ShockExpansion edge failed
- became obvious sideline candidate

RangeReclaim in v2p63:
- 746 trades
- Net -236.23
- ShockExpansion remained positive
- Transition became negative
- should be kept away from established directional environments

v2p64 — CREATED, NOT YET TESTED
-------------------------------
Live/probation roster:
- RangeReclaim
- MomentumContinuation — probation pass 3
- ExhaustionReset — probation pass 3
- LongStructureContinuation — NEW, probation pass 1

Sidelined/shadow roster:
- TrendRetest
- Pullback
- CompressionRelease
- ShortHold
- DelayedConfirmation

LongStructureContinuation purpose:
- dedicated clean long-directional continuation specialist
- intentionally asymmetric complement to MomentumContinuation's demonstrated short-side strength
- should require strong persistence, structural stability, orderly expansion, and relatively low noise

v2p64 intent:
- preserve the two new algorithms that turned profitable in v2p63
- remove major current drags from live routing
- add one new long-directional candidate
- keep dormant/shadow framework active
- keep trade-management settings unchanged for cleaner attribution

CURRENT SUB-EA STATUS SUMMARY
-----------------------------
RangeReclaim
- role: change-of-state / reclaim / non-established-direction specialist
- often positive in ShockExpansion
- repeatedly harmful in established directional states
- live in v2p64

MomentumContinuation
- new discovery-cycle algorithm
- pass 2 profitable +170.81
- strongest evidence in ShortBiasDirectional
- pass 3 in v2p64
- should remain narrow until durable

ExhaustionReset
- new discovery-cycle algorithm
- pass 1 +51.53
- pass 2 +318.96
- strongest emerging candidate
- directional/shock specialization
- pass 3 in v2p64

LongStructureContinuation
- new in v2p64
- pass 1
- long-directional continuation specialist

TrendRetest
- once showed repeated ShockExpansion strength
- deteriorated later
- sidelined in v2p64 but remains shadow evaluated

CompressionRelease
- occasional historical positive pockets
- major drag in v2p63
- sidelined in v2p64 but remains shadow evaluated

Pullback
- dormant metrics once justified controlled reactivation
- v2p61 live reactivation failed
- sidelined with cooldown/history penalty

DelayedConfirmation
- once had strong dormant metrics
- live reactivation failed badly
- sidelined with cooldown/history penalty

ShortHold
- long-term sidelined
- sometimes strong shadow win rate but small samples

PERMANENT RESEARCH REFERENCE — WOODIES CCI CLUB
------------------------------------------------
Source file:
Woodies_CCI_Club.pdf
Remembered Library ID:
libfile_43dd4448ef348191961c5c4fe94b50dc

Standing user instruction:
Treat this document strictly as a permanent research/reference source.
Do NOT copy Woodies CCI as a complete trading system.
Track any useful technical developments derived from it.
Include both the source reference and the derived technical concepts in all future transfer/recovery summaries.

Any Woodies-inspired algorithm must still follow:
- independent testing
- behavior evaluation
- 3–6 pass probation
- PF<1.10 discovery governance
- dormant/shadow evaluation if sidelined

Core technical components in the Woodies document:
- 14-period CCI
- 6-period Turbo CCI / TCCI
- Zero Line
- +/-100 and +/-200 CCI zones
- 25-period LSMA
- Sidewinder
- Chop Zone

Permanent Woodies-derived research concepts:
1. Zero-Line Reject (ZLR)
   - established trend
   - CCI retraces toward/through zero
   - turns back with trend
   - research interpretation: controlled continuation after retracement

2. Trend Line Break (TLB)
   - oscillator structure line across CCI peaks/troughs
   - structure break
   - research interpretation: mathematical oscillator/momentum structure break

3. Tony Trade
   - momentum failure around +/-100
   - failure to continue
   - movement back toward trend direction
   - research interpretation: momentum-failure / exhaustion confirmation

4. GB100
   - deeper ZLR
   - CCI moves beyond +/-100 then returns toward original trend
   - research interpretation: deep retracement / overshoot-and-return

5. Famir
   - ZLR-like setup immediately fails and reverses
   - often with LSMA agreement
   - research interpretation: failed-continuation reversal

6. Vegas Trade
   - CCI extended beyond +/-200
   - returns through zero
   - rounded multi-bar structure
   - research interpretation: extreme-extension exhaustion/reversal

7. Ghost
   - three-peak / three-valley CCI structure
   - head-and-shoulders-like oscillator geometry
   - neckline break
   - research interpretation: three-swing oscillator reversal

Behavior hierarchy implied by Woodies material:
trend established -> retracement -> continuation
trend established -> retracement fails -> reversal
extreme extension -> momentum deterioration -> reversal
sideways/choppy -> do not treat as trend

Standing Woodies-inspired candidate pool for future discovery slots:
- CCI Zero-Line Continuation
- CCI Structural Break / TLB
- CCI Failure/Reversal family using Famir/Tony/Vegas ideas

Do NOT automatically add these. They are permanent research candidates.

NAMING / FILE RULES
-------------------
EA source:
FXD_AdaptiveEA_v2pNN.mq4

SET:
FXD_AdaptiveEA_v2pNN_2010_2019_DEV.set

Do not append words such as _fixed, _behavior, _final, _new.
Descriptive purpose belongs in top source comments.

RunTag must match current version, e.g.:
ADAPTIVE_EA_V2P64_2010_2019_DEV

Logs should generally be versionless and overwrite each run:
FXD_AdaptiveEA_TradeLog_<Symbol>_<Period>.csv
FXD_AdaptiveEA_AlgoSummary_<Symbol>_<Period>.csv
FXD_AdaptiveEA_StateLog_<Symbol>_<Period>.csv

Pure compile fixes:
- same version
- same filename

If adding many CSV fields in MQL4, remember FileWrite has a parameter-count limit; use incremental/multiple writes rather than dropping fields.

REPORTING RULES
---------------
Report sub-EA first.
Use:
- green / improved / promising
- yellow / mixed / inconclusive
- red / failed / harmful

Per sub-EA include when available:
- status
- probation pass
- trades
- win %
- net PnL
- attributed CAGR
- MaxDD
- WorstTradeDDImpact
- AvgLossDDImpact
- AvgDDImpactPerTrade
- behavior-specific performance
- dormant relevance/potential metrics if sidelined

When an algorithm flips from positive to negative, investigate WHY before discarding.

HOW TO ANALYZE THE NEXT TEST
----------------------------
When v2p64 tester output + AlgoSummary + StateLog + TradeLog arrive:

1. Confirm RunTag/version because the user sometimes reruns older builds after breaks.
2. Report aggregate Net / PF / DD / trades / win rate / expected payoff.
3. Produce sub-EA-first table.
4. Break each live/probation sub-EA down by behavior/descriptors.
5. Specifically check:
   - MomentumContinuation pass 3: does ShortBiasDirectional edge persist?
   - ExhaustionReset pass 3: does directional/shock profitability persist?
   - LongStructureContinuation pass 1: any useful long-directional specialty?
   - RangeReclaim: are established-directional losses now controlled?
6. Inspect dormant ranks and cooldown penalties.
7. Apply PF rule.
8. Do not discard new algorithms before 3–6 passes unless catastrophic.

STYLE / INTERACTION PREFERENCES
-------------------------------
- direct and technical
- compact but substantive
- avoid re-explaining settled rules
- explain why changes are being made
- avoid endless tiny tweaks when material algorithm change is indicated
- preserve research history
- keep sidelined algorithms available for future regimes
- focus on behavior relevance and algorithm attribution
- do not data fit

ONE-PARAGRAPH RESUME POINT
--------------------------
The project has evolved from broad multi-algorithm competition into a behavior-router architecture using continuous market descriptors, confidence classes, strict live/sidelined separation, dormant shadow evaluation, Profitability Potential, Relevance Persistence, Replacement Readiness, ranking, and reactivation cooldowns. PF remains below the standing 1.10 sufficiency threshold, so algorithm discovery remains active. The strongest recent tested build is v2p63 (Net -1429.44, PF 0.93, MaxDD 16.42%). Two new algorithms introduced in v2p62 improved strongly in v2p63: MomentumContinuation became profitable as a ShortBiasDirectional specialist (+170.81 overall), and ExhaustionReset became strongly profitable (+318.96 overall). CompressionRelease and TrendRetest became major drags and are sidelined in v2p64. v2p64, created but not yet tested, keeps RangeReclaim live, advances MomentumContinuation and ExhaustionReset to probation pass 3, adds LongStructureContinuation as a new pass-1 long-directional specialist, and keeps Pullback/CompressionRelease/TrendRetest/ShortHold/DelayedConfirmation sidelined but continuously evaluated. Woodies_CCI_Club.pdf is a permanent research source only; its CCI continuation/reversal concepts are permanent candidates for future sub-EA or behavior-descriptor research but must not be copied wholesale.

===================================================================
END OF ADDENDUM / COMPLETE TRANSFER CONTEXT
===================================================================
