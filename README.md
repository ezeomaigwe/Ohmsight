# Ohmsight

## Ohmsight Risk-Based Electrical Review Model [Excel copy]
### Deficiency taxonomy, evidence-based risk scoring, and code mapping. Version 0.2, September 2026. Author: Ezeoma (Lewis) Igwe.

#### What this workbook does
1. Taxonomy: 60 recurring electrical design deficiencies in 7 groups (general documentation, PV, energy storage, emergency and standby, fire alarm, service and distribution, load calculations).
2. Risk model: Risk = Severity score x Frequency score (maximum 25). Deficiencies are ranked into a 'review first' order and three priority tiers.
3. Code mapping: each deficiency is linked to NEC 2023 and California Title 24 sections by number only. No code text is reproduced.

#### How frequency is scored (the evidence method)
Frequency is not guessed. It is scored from published sources listed on the Sources tab:
   - AHJ checklists: how many independent jurisdiction or code-body plan review checklists require or flag the item (CA, VA, AZ, WI, and ICC).
   - Industry sources: how many plan-set or engineering sources describe the item as a common reason plans are returned.
   - Top problem: whether any source names it as the most common or most often overlooked problem.
The rules that turn these counts into a 1 to 5 score are on the Scales tab. The Field adjustment column (-2 to +2) lets the reviewer adjust each score from measured project data, with a note explaining why.

#### Tabs
Taxonomy and Risk: the main table. Yellow cells are inputs.
Review First: every deficiency in rank order. Updates automatically.
Summary by System: counts, Tier 1 items, and average risk per group. Updates automatically.
Sources: the evidence register with links.
Scales: severity weights, frequency evidence rules, and tier thresholds.

#### Limits of this version
A. Frequency reflects how often an item appears in published checklists and industry reporting, not a measured rate from reviewed projects. The next version will calibrate it with results from sample projects and pilot jurisdictions using the Field adjustment column.
B. Sources are weighted toward residential PV, where public data is richest. Low scores for items such as EV load or arc energy reduction mean little published evidence, not proof that the problem is rare.
C. Industry articles (S9 to S11) are commercial sources. Their counts are used, but figures they quote without citation (for example, a claimed 30% to 40% rejection share for PV conductor sizing) are not used as numeric inputs.
D. Reference check column: 'Confirmed in source' means a listed source cites the same section for the same requirement. 'Needs check' means a standard section that should still be confirmed against the adopted edition before publication.
E. No agency records were used. All data comes from public documents.

#### Code editions referenced
NEC 2023 (NFPA 70), the base of the 2025 California Electrical Code (Title 24, Part 3), effective January 1, 2026. Other Title 24 parts: Part 2 CBC, Part 2.5 CRC, Part 6 Energy Code, Part 9 CFC, Part 11 CALGreen. NFPA 72 and NFPA 110 where the electrical code does not set the requirement.
The NEC column is the part of the model that transfers directly to any U.S. jurisdiction that adopts the NEC.
