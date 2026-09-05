# Limitations

DRAFT FOR HUMAN REVIEW. Read this before using the data.

These are stated plainly because several of them are severe. Items 1 to 4 mean
the conditions of collection are not fully recoverable from the record.

1. **The model identifier as served was not recorded.** The platform column
   names a product, ChatGPT, Claude, Perplexity or Google AI Overviews, not the
   model that answered. Each of these products routed requests to more than one
   model during the collection window, and the routing was not visible to the
   collector and was not logged. No row can be attributed to a specific model
   version. One row, R042, happens to note that a query was run first on one
   Claude model and then on another, which shows the variation was real and
   otherwise unrecorded.

2. **Grounding and web-search state was not recorded.** Whether an answer was
   generated from model weights alone or from live retrieval was not captured,
   and on several of these products it was not exposed to the user. The presence
   of source URLs in a row is suggestive but not decisive, because sources may
   be surfaced by the product interface rather than used in generation. Answers
   produced with retrieval and answers produced without it are mixed together in
   this file and cannot be separated after the fact.

3. **Run time is present on 104 of the 200 rows.** The remaining 96 rows carry a
   date but no clock time. Ordering within a day cannot be established for
   those rows. Run date is present on all 200.

4. **Responses are excerpts, not full captures.** The `Raw Response Excerpt`
   column holds a fragment selected by the collecting analyst, not a verbatim
   record of the answer. On 97 of the 200 rows it is empty and the only account
   of the answer is the analyst's note. Anything absent from an excerpt cannot
   be treated as absent from the original answer. Excerpt selection was not
   blind and was made by the same person recording the observations.

5. **Organization identities are withheld.** Organizations appear only as roster
   identifiers. Anyone working from these files alone cannot tell which
   organization a row concerns. The mapping is available to researchers on
   request, as set out in README.md. Until it is supplied, findings can be
   stated about the structure and distribution of outputs but not about any
   particular organization.

6. **Published probe figures measure the organic answer layer only.** Every
   figure derived from this collection describes what the assistants returned as
   answer text. No arm of this collection could observe paid placements.
   Advertising, sponsored positions and any commercial arrangement affecting
   what an assistant surfaces are outside what was measured and outside what
   could have been measured with this method. A figure from this data is not a
   statement about total visibility on these platforms.

7. **One pass, three dates, no repetition.** Each query was put to each
   assistant once. Captures fall on 2026-04-30, 2026-05-11 and 2026-05-12.
   Nothing was re-run to test stability, so run-to-run variance is unmeasured
   and cannot be distinguished from differences between platforms or queries.

8. **One patient was removed, not coded.** A model output named a private
   individual alongside their medical diagnosis. Both occurrences were deleted
   and marked `[patient case detail removed]`. Surrounding statistics were kept.
   The record is therefore not a complete transcript of what was returned, and
   the removal is deliberate.

9. **Location detail can narrow a coded identifier.** Coding removed names, not
   places. Notes and excerpts still carry cities, countries and venues drawn
   from the answers. A reader who knows the market may be able to infer some
   identities from that detail. Coding reduces the risk of circulating
   unverified claims against named companies. It is not anonymization and should
   not be relied on as such.

10. **Analyst notes are interpretation, not observation.** The `Notes` column
    mixes what was seen with what the analyst concluded, including scores,
    judgments about integrity and claims about cross-platform patterns. Those
    readings were not independently checked. Where a note and an excerpt
    disagree, the excerpt is the closer record.

11. **Collection was not uniform across rows.** 180 rows were recorded by one
    person and 20 by an assisted tooling session, and capture method varies by
    row, including manual paste and markdown export. No screenshots are included
    in this deposit, so entries in `Screenshot Path` cannot be checked against an
    image.

12. **Geography and language were not controlled.** Queries were issued from one
    location without varying account state or language. Several answers show
    signs of geographic personalization. Results for a query naming a place were
    not collected from that place.
