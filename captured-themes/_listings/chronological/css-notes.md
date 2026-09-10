# chronological — styling analysis (2026-09-09)

**No Layer 1 rules needed.** On live this layout is the stock Plone 4 folder listing
(`dl > dt.summary + dd.description`, byline inline after the title) with no
`ploneCustom.css` rule of its own; locally `chronological.pt` emits the stock Plone 6
listing markup (`.entries > article.mb-3 > .url / .documentByLine / .description`),
which Barceloneta styles. That is the accepted Plone 6 equivalent — nothing to restate.

## Markup divergences (flag to lp.content, not CSS)

1. `.documentByLine` prints the raw ISO timestamp (`2026-08-23T03:36:02+00:00`); live
   prints `Mar 10, 2017 03:18 PM`. The template should run the date through the
   long-format localizer.
2. Item order differs from live because the sort key is `modified`, and every imported
   item carries the import time (2026-08-23), not its source modification date. Import
   gap — the layout cannot be truly chronological until modification dates are migrated.
3. Byline shows "by gbee" with a member link locally vs plain text live — fine.

## Verification (2026-09-09)

Local 1660 admin vs dev 1440 and 390: title, per-item title link, byline, description
all present in the same order of elements; only the two divergences above differ.
