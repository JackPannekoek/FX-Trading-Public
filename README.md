# FX-Trading-Public
Public copy of private internal EA

Project overview
To Be Added

Architecture
To Be Added

Governance
To Be Added

Current status
To Be Added

Repository layout
To Be Added

Agent Instructions


**Authoritative Source Rules**
Priority order:

Latest MQ4 source
Latest test results
Logs
Recovery context
Historical discussion
Where conflicts occur, actual source code and test evidence take precedence.



FXD Adaptive EA - AI Agent Instructions
Purpose
This repository contains the FXD Adaptive EA research project.

The project objective is not to optimize a single trading system.

The objective is to develop a genuinely adaptive Expert Advisor capable of:

Describing current market behavior from observable candle statistics.
Detecting changes in market behavior.
Selecting the specialist trading algorithm currently best suited to that behavior.
Keeping inactive algorithms under continuous shadow evaluation.
Reactivating previously useful algorithms when market conditions change.
Discovering new algorithms when the current roster proves inadequate.
The system should evolve as a specialist ecosystem rather than a monolithic EA.

Authoritative Sources
Priority order:

Latest MQ4 source code
Latest test results
Latest log files
Recovery / transfer documentation
Historical discussions
If a conflict exists:

Current MQ4 source and current test evidence override written summaries.

Core Design Principles
Behavior First
Adaptation must be driven by:

Current market behavior
Current market structure
Current market statistics
Adaptation must NOT be driven primarily by:

Recent PnL
Recent trade results
Calendar periods
Date ranges
Behavior recognition is more important than algorithm selection.

Continuous Descriptors Preferred
Continuous behavior descriptors are preferred over coarse state labels.

Examples include:

Persistence
Directional agreement
Expansion
Compression
Noise
Stability
Path efficiency
Overlap
Follow-through
Directional asymmetry
State labels are useful summaries but should not become the primary routing mechanism.

Router Philosophy
Desired flow:

Market Features -> Behavior Descriptors -> Behavior Interpretation -> Eligible Specialists -> Specialist Ranking -> Router Confidence -> Trade Intent

The router is permitted to remain uncertain.

Do not force participation simply because no specialist is clearly superior.

Market-State Concepts
Possible summarized states include:

UNKNOWN
TRANSITION
LongBiasDirectional
ShortBiasDirectional
BalancedExpansion
ShockExpansion
LowVolCompression
These represent summaries.

They are not sufficiently rich to replace descriptor-driven routing.

Specialist Architecture
The project intentionally maintains multiple specialist algorithms.

A specialist should have:

Explicit market thesis
Defined preferred conditions
Defined avoidance conditions
Identifiable contribution
Avoid turning specialists into generic all-market strategies.

Live and Dormant Separation
A sidelined specialist:

Cannot open live trades
Cannot be selected by the router
Cannot become a fallback selection
A sidelined specialist:

Must continue receiving descriptor relevance evaluation
Must continue receiving shadow evaluation
Must continue maintaining dormant metrics
Strict separation is a permanent architectural requirement.

Dormant Evaluation Framework
The dormant framework exists to identify future relevance.

Key metrics include:

RelevanceFactor
DescriptorRelevance
ShadowTrades
ShadowWins
ShadowWinRatePct
ShadowNetR
ProfitabilityPotential
RelevancePersistence
ReplacementReadiness
ReactivationRank
ReplacementRank
ReadinessRank
ReactivationCooldownPenalty
Do not collapse relevance and profitability into a single measure.

They are related but distinct concepts.

PF Governance Rule
Profit Factor remains a governance trigger.

PF < 1.10
Continue algorithm-discovery research.

The current roster cannot be assumed sufficient.

Exception
If a dormant candidate demonstrates strong:

ProfitabilityPotential
ReplacementReadiness
Shadow evidence
then evaluate that candidate before introducing a completely new algorithm.

Reactivation Failure
If a dormant candidate is reactivated and fails live:

apply cooldown penalty
return to dormant status
resume algorithm-discovery process if PF remains below 1.10
New Algorithm Rule
A new specialist algorithm normally receives:

3-6 evaluation passes

before removal.

Exceptions:

Catastrophic failure
Major architectural incompatibility
Severe evidence of structural weakness
Avoid discarding new specialists prematurely.

Current Research Direction
The project evolved from:

Broad algorithm competition

toward:

Behavior-driven specialist routing.

Recent evidence suggests:

Specialist selection quality matters more than trade frequency.
Router quality matters more than trade-management changes.
Continuous descriptors outperform coarse-state-only approaches.
Preserve this direction unless strong evidence suggests otherwise.

Risk and Optimization Guidance
Avoid:

Calendar fitting
Date-region optimization
Period-specific tuning
Excessive threshold optimization
Prefer:

Market-behavior explanations
Descriptor-driven logic
Generalizable structure
Versioning Rules
MQ4 Naming:

FXD_AdaptiveEA_v2pNN.mq4

SET Naming:

FXD_AdaptiveEA_v2pNN_2010_2019_DEV.set

RunTag:

ADAPTIVE_EA_V2PNN_2010_2019_DEV

Compile-Fix Rule
Compile fixes alone do NOT justify a version increase.

If correcting syntax or compile issues:

Keep same version.
Keep same filename.
Keep same RunTag.
Version numbers advance only when logic changes.

Logging Rules
Preferred logs:

FXD_AdaptiveEA_TradeLog_

FXD_AdaptiveEA_StateLog_

FXD_AdaptiveEA_AlgoSummary_

Logs should generally overwrite per run.

Avoid version-specific log filenames unless intentionally preserving a snapshot.

Reporting Priorities
When analyzing test results:

Confirm version and RunTag.
Report overall metrics.
Report specialist attribution.
Report behavior-specific performance.
Review dormant rankings.
Apply governance rules.
Recommend next action.
Specialist attribution is often more important than aggregate PF.

Woodies Research Reference
Permanent source:

Woodies_CCI_Club.pdf

Purpose:

Research reference only.

Do NOT clone or directly reproduce Woodies as a system.

Potential future inspiration areas:

Zero-Line Reject
GB100
Tony Trade concepts
Famir concepts
Vegas concepts
TLB concepts
Any derived specialist must still follow:

Independent implementation
Independent testing
Probation process
Attribution analysis
Dormant evaluation process
Source-Code Maintenance
Preferred source-code organization:

SECTION 01 - Version / Change Log SECTION 02 - User Inputs SECTION 03 - Enums / Constants SECTION 04 - Data Structures SECTION 05 - Global State SECTION 06 - Utilities SECTION 07 - Feature Engine SECTION 08 - Descriptor Engine SECTION 09 - Behavior Interpretation SECTION 10 - Router SECTION 11+ - Specialists SECTION XX - Logging / Reporting

Future changes should preferably replace complete sections rather than isolated line edits.

This minimizes:

Copy/paste errors
Merge mistakes
Version drift
Partial updates
Final Principle
The ultimate goal is not to find a perfect strategy.

The ultimate goal is to build an adaptive specialist ecosystem capable of recognizing changing market behavior and continuously improving specialist participation over time.
