# album_view (atct_album_view / galleryview) — notes (2026-09-27)

`assign_folder_views.py` (PR #71) maps `atct_album_view` (1) and `galleryview` (9) to
Barceloneta's stock `album_view`. **Live differs structurally:** the `galleryview`
folders ran collective.plonetruegallery — a slideshow with caption bar and thumbnail
strip (see `screenshots/album-aquatics-photo-gallery-live-1440.png`); `atct_album_view`
was the Plone 4 polaroid album (`.photoAlbumEntry` with `polaroid-single.png`
backgrounds). Neither can be reproduced with CSS over the Barceloneta card grid.

Decision this run: **no Layer 1 rules** — local album_view (responsive Bootstrap card
grid, 5-up at 1660, image + title + description + View link) is a reasonable stand-in.
Flag for the user: choose a gallery add-on (or accept the card grid) for the 10 folders.

| Slug | Sub-site | Local (plain URL) | Live |
|---|---|---|---|
| album-aquatics-photo-gallery | aquatics | `/Plone/networks/working-lands-for-wildlife/landscapes-wildlife/landscapes/aquatics/wildlife/bog-turtle/information-materials/photo-gallery` (31 Images) | https://dev.landscapepartnership.org/…/bog-turtle/information-materials/photo-gallery (plonetruegallery slideshow) |
