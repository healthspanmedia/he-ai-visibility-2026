# AI Visibility 2026: an observational record of consumer AI assistant outputs

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22635989.svg)](https://doi.org/10.5281/zenodo.22635989)

## What this is

A dated observational record of what four consumer AI assistants returned when
asked a fixed set of 50 queries about longevity and preventive health clinics.
All 200 captures fall on three dates: 2026-04-30, 2026-05-11 and 2026-05-12.
A round of identifier corrections was applied 2026-05-15. There are no other
collection dates.

The four assistants are ChatGPT, Claude, Perplexity and Google AI Overviews.
Each of the 50 queries was put to each assistant once, giving 200 observations.
The queries span five categories: brand-direct, category, service or protocol,
comparison and patient research.

The record holds what was returned: which organizations were named, which
sources were surfaced, an excerpt of the answer text where one was kept, and
the collecting analyst's notes on each run.

## What this is not

This is not a benchmark, a ranking, a league table or an evaluation of any
organization. It does not rate providers and it does not measure quality of
care. It is not a measurement of any assistant's accuracy, and it is not a
controlled experiment.

It is not a complete capture. Most cells in the response column hold an excerpt
rather than the full answer, and 97 of the 200 rows carry no excerpt at all.
Several conditions that would be needed to run the same collection again were
not recorded at the time. LIMITATIONS.md sets these out in full and should be
read before the data is used for anything.

A single pass on a single date is a snapshot. Assistant outputs change with the
model version served, the retrieval index behind it, the account, the location
and the moment. Nothing here should be read as a stable property of any
assistant or of any organization named in it.

## Why identities are coded

Organizations appear as roster identifiers of the form HM-nnn, never by name.
Forty-four distinct identifiers appear across these files.

The reason is that the record contains machine-generated claims about named
commercial organizations, including pricing, clinical positioning and
comparative judgments, none of which has been verified as true. Publishing an
unverified machine claim next to a company's name would misrepresent that
company, whatever caveats surround it. Coding lets the structure of the
observations be examined without putting unverified assertions into
circulation against identifiable businesses.

The mapping from roster identifier to organization is held by the publisher and
is available to researchers on request. Requests go to the contact in
NOTICE.md.

The coding is applied to organizations. People named in a business or
professional capacity, such as founders, clinicians, researchers and podcast
hosts, are left as they appear, because they are named in the source material
as public professional figures rather than as private individuals. One patient
named in a model output has been removed entirely rather than coded. See
LIMITATIONS.md item 8.

## Files

| File | Rows | What it holds |
| --- | --- | --- |
| observation_log.csv | 200 | One row per query and assistant pair. The primary record. |
| reject_log.csv | 75 | Runs excluded from scoring, with the reason for exclusion. |
| query_master.csv | 50 | The fixed query set, with intent and prior hypothesis. |
| calibration_sample.csv | 23 | The subset used to calibrate the collection method. |

CODEBOOK.md describes every column of every file.

## Status

Version 1.0.0, released 2026-09-07. Two DOIs are registered with Zenodo.

| DOI | What it resolves to |
| --- | --- |
| [10.5281/zenodo.22635989](https://doi.org/10.5281/zenodo.22635989) | The concept DOI, covering all versions. Always resolves to the latest version. |
| [10.5281/zenodo.22635990](https://doi.org/10.5281/zenodo.22635990) | The version DOI for v1.0.0. Always resolves to this release and no other. |

Cite the concept DOI, 10.5281/zenodo.22635989, for all versions. Use the
version DOI only when a citation has to be pinned to v1.0.0 specifically.
