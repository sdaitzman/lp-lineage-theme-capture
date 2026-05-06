# Equity & Inclusion — Style Guide

**Status: BLOCKED — capture not performed.**

## Capture notes

The production URL for this sub-site is **access-restricted** and cannot be
reached anonymously. As a result, no Phase 1 capture material was collected
on this run.

### What was attempted

| Attempt | URL | Result |
|---|---|---|
| Direct load (Playwright) | `https://landscapepartnership.org/key-issues/equity-inclusion/` | 302 → `acl_users/credentials_cookie_auth/require_login` (Plone login form) |
| Direct load, no trailing slash | `https://landscapepartnership.org/key-issues/equity-inclusion` | Same login redirect |
| HTTP HEAD (curl) | `https://landscapepartnership.org/key-issues/equity-inclusion/` | `HTTP/2 401`, `bobo-exception-type: zExceptions.unauthorized.Unauthorized`, `www-authenticate: basic realm="Zope"` |
| HTTP HEAD, no trailing slash | `https://landscapepartnership.org/key-issues/equity-inclusion` | Same 401 / Zope Unauthorized |
| Parent listing | `https://landscapepartnership.org/key-issues` | Loads, but does not list "Equity & Inclusion" — page is hidden from anonymous nav |
| Sitemap | `https://landscapepartnership.org/sitemap` | No `equity` links present anonymously |
| Search | `https://landscapepartnership.org/@@search?SearchableText=equity+inclusion` | Returns content tagged "Equity and Inclusion", but the key-issue site itself is not in the results; only an unrelated organization page (`/networks/organizations/equity-and-inclusion`) and a training video |

The page exists on production (Zope returns a 401 with a login challenge,
not a 404), but every URL under `/key-issues/equity-inclusion` requires
authentication.

### Why no capture was produced

Per `plans/subsite-theme-replication.md`:

> **Always capture from production. Never capture from
> `dev.landscapepartnership.org`.** […] If a sub-site only exists on dev,
> stop and confirm with the user before proceeding — that's a signal the
> work isn't ready for replication.

This sub-site exists on production but is gated behind a Plone login. No
credentials were available in this session, and the plan explicitly forbids
capturing from `dev.landscapepartnership.org`. Producing a partial or
fabricated capture would mislead Phases 2–4, so capture was halted instead.

### Pages that would need to be enumerated (once access is restored)

Currently unknown — the nav, sidebar, and footer link inventory cannot be
read until the landing page renders.

### To unblock

One of the following must happen before re-running this plan:

1. **Provide production credentials** for an account with read access to
   `/key-issues/equity-inclusion/` (Plone login at
   `https://landscapepartnership.org/login`). The capture script can then
   authenticate via Playwright and proceed with §1.1 – §1.6 unchanged.
2. **Publish the page anonymously** on production (workflow → Publish), so
   Phase 1 can run against the live URL with no credentials.
3. **Confirm an alternative production host** for this sub-site (analogous
   to `bobscapes.org` / `workinglandsforwildlife.org`). If one exists, add
   it to the roster's URL column and re-run capture against that host.

Until one of those is true, this directory should remain empty (apart from
this note), and `equity-inclusion` should not move into Phase 2.

## Page inventory

_Empty — no pages captured._

## Color palette

_Not captured._

## Typography

_Not captured._

## Layout & structure

_Not captured._

## Navigation

_Not captured._

## Buttons

_Not captured._

## Content blocks

_Not captured._

## Footer

_Not captured._

## Responsive breakpoints

_Not captured._

## Google Fonts

_Not captured._

## Print styles

_Not captured._
