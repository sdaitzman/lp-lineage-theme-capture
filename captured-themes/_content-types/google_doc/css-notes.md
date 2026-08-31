# google_doc — styling analysis (2026-08-31)

**N/A — nothing to style.** `gdoc_view` (a browser view,
`lp.content/browser/gdoc_view.pt`) renders a bare XHTML **frameset**: a 215px
`@@header_frame` row plus a frame loading the external Google Doc URL. No
Plone body classes, no theme CSS applies inside the frames, and Diazo does not
transform framesets. The header frame (`gdoc_header_frame.pt`) carries its own
minimal markup; restyling it would be template work in `lp.content`, not theme
SCSS.

Sample: `key-issues/anchor/anchor-resources/appendix-partner-resources-google-doc`
(anchor sub-site; local 200; live counterpart is **private** → no anonymous
reference capture). 45 instances at last count.

Checklist status: marked N/A for all sub-sites.
