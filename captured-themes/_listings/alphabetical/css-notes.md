# alphabetical — styling analysis (2026-09-10)

**No Layer 1 rules needed.** The template emits the stock Plone 6 listing markup
(`.entries > article.mb-3 > .url / .documentByLine / .description`), the same as
`chronological.pt`, which Barceloneta styles; there is no live `ploneCustom.css` rule for the
Plone-4 `folder_contents_alpha` layout either.

## Markup divergences (flag to lp.content, not CSS)

1. `.documentByLine` prints the raw ISO timestamp (`2026-08-23T03:42:36+00:00`) — same as
   chronological; the template should localise the date.
2. Both sampled folders hold only one or two children locally (one of them a test folder
   named "fsdgss"), so alphabetical ordering could not be exercised; the sort key itself is
   the script's, not CSS.

## Verification (2026-09-10)

Local 1660 admin only (no live counterpart): title, description, one article per child with
title link, byline and description render; body class `template-alphabetical`. Nothing to
compare against until a public `folder_contents_alpha` folder exists on dev.
