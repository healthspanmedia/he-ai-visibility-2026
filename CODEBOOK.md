# Codebook

DRAFT FOR HUMAN REVIEW.

## Roster identifier convention

Every organization is written as `HM-nnn`, a stable identifier from the
publisher's internal roster. Identifiers are not sequential, not ordered by
rank and not ordered by anything else that can be read off the number. A gap in
the numbering carries no meaning.

Inside free-text cells an identifier appears in square brackets, `[HM-001]`,
marking a substitution made during preparation. Outside free text, in the
`Clinics Mentioned (clinic_ids)` and `clinic_id` columns, identifiers appear
bare and comma separated, as they were recorded at collection.

Two conventions in the source survive in the notes and should not be read as
errors:

- `ID-CORR <date>: HM-aaa->HM-bbb` records that an identifier assigned during
  collection was corrected against the raw capture on that date. Both the old
  and the new identifier are kept so the correction stays visible.
- A note may say an organization is in the research queue, or not among the 25
  scored subjects. The record covers more organizations than it scores.

Forty-four distinct identifiers appear. Twenty-five of them are the scored
subjects. The rest were named in model output or in analyst notes and carry an
identifier because the publisher's roster already held one.

Organizations that appear in the outputs without a roster identifier are left
under their own names. They are third parties surfaced by the assistants, not
subjects of this collection, and inventing identifiers for them would assert a
roster membership that does not exist.

## observation_log.csv

200 rows, one per query and assistant pair.

| Column | Type | Description |
| --- | --- | --- |
| Run ID | string | Unique run key, `Rnnn`. Ordering is collection order, not time order. |
| Query ID | string | Key into query_master.csv. `A01` to `E10`. |
| Query Text | string | The query as put to the assistant. Coded where it names an organization. |
| Category | string | One of five. See below. |
| Platform | string | ChatGPT, Claude, Perplexity or Google AI Overviews. 50 runs each. |
| Run Date | ISO date | Date of capture. Populated on all 200 rows. |
| Run Time | string | Clock time of capture. Populated on 104 of 200 rows. Empty elsewhere. |
| Scorer | string | Who recorded the run. `Sumesh` on 180 rows, `Cowork` on 20. `Cowork` is an assisted tooling session, not a second human. |
| Screenshot Path | string | Capture method, or a note that no screenshot exists. Google AI Overviews rows may record whether an overview triggered. No image files are included in this deposit. |
| Top Source 1 to 5 (URL) | string | Sources the assistant surfaced, in the order shown. A parenthesized entry is the analyst's description of a source rather than a URL. Coded where it names an organization. |
| Clinics Mentioned (clinic_ids) | string | Comma separated roster identifiers named in the answer. May instead hold a parenthesized note such as `(none of 25)`. |
| Raw Response Excerpt | string | Excerpt of the assistant's answer. Model text only. Empty on 97 of 200 rows. Never a full capture. |
| Notes | string | The analyst's observations: visibility and integrity readings, absences, cross-platform patterns and roster updates. Analyst voice throughout, not model output. |

Categories: `A — Brand-direct`, `B — Category`, `C — Service/Protocol`,
`D — Comparison`, `E — Patient research`. Forty runs each.

Three rows carry a line beginning `ANALYST ANNOTATION (moved from Raw Response
Excerpt)` in Notes. In the source these annotations sat at the head of the
excerpt cell, mixed in with model text. They were moved during preparation so
the excerpt column holds model text and nothing else. The rows are R113, R117
and R120. On R120 the whole cell was annotation and no model text was ever
captured, so the excerpt is empty.

## reject_log.csv

75 rows. Runs excluded from scoring, kept so the exclusions are inspectable.

| Column | Type | Description |
| --- | --- | --- |
| kind | string | Reason for exclusion. Four values, below. |
| run_id | string | Joins to `Run ID` in observation_log.csv. |
| query_id | string | Joins to `Query ID` in query_master.csv. |
| platform | string | As in observation_log.csv. |
| clinic_id | string | Roster identifiers involved. May be empty. |
| excerpt | string | Text supporting the exclusion. Coded. |

| kind | Rows | Meaning |
| --- | --- | --- |
| zero-observation run | 32 | Nothing scoreable was returned or captured. |
| clinic recorded absent | 17 | The run recorded an absence, which carries no score. |
| no VISIBILITY: segment and no prose score | 13 | The note lacks the structured segment a score is read from. |
| clinic named, no numeric score | 13 | An organization was named but no score was recorded against it. |

## query_master.csv

50 rows. The fixed query set.

| Column | Type | Description |
| --- | --- | --- |
| Query ID | string | `A01` to `E10`. |
| Category | string | As above. |
| Query Text | string | The query. Coded where it names an organization. |
| Intent | string | What the query was meant to test. Coded. |
| Geo-specific? | Y/N | Whether the query names a place. |
| Skeptical framing? | Y/N | Whether the query is worded to invite criticism. |
| Practitioner-name? | Y/N | Whether the query names a person. |
| Expected Winners (hypothesis) | string | Who the analyst expected to surface, recorded before collection. A prior, not a finding. Coded. |

## calibration_sample.csv

23 rows. The subset run first to calibrate the collection method.

| Column | Type | Description |
| --- | --- | --- |
| Order | integer | Intended run order within calibration. |
| Query ID | string | Joins to query_master.csv. |
| Category | string | As above. |
| Query Text (copy-paste this) | string | The query as issued. Coded. |
| Edge cases this query tests | string | What the query was chosen to stress. Coded. |
| Why included in calibration | string | Rationale for inclusion. Coded. |

## Preparation applied to every file

1. Organization names replaced with `[HM-nnn]`, matching on the roster name and
   on trading names, abbreviations, own domains and other variants.
2. One named patient removed entirely rather than coded, replaced with
   `[patient case detail removed]`. Surrounding statistics were kept.
3. Analyst annotations moved out of the excerpt column into Notes on three rows.

No rows were dropped, merged or reordered. No numeric value was altered.
