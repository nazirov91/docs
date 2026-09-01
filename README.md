# BeRocker Knowledge Base

The public help site for [BeRocker CRM](https://app.berocker.com), published with
[Mintlify](https://mintlify.com) at **https://help.berocker.com**.

## Structure

| Path | What is in it |
| --- | --- |
| `index.mdx`, `quickstart.mdx` | Landing page and the 7-step quickstart |
| `get-started/` | Tour of the CRM, the lead pipeline, the setup checklist |
| `onboarding/steps/` | The four first-week onboarding steps |
| `using/` | One page per screen: Inbox, Shipments, Follow up, Dispatch, Interactions, Carriers, Customers, Terminals, Accounting, Dashboard, AI Assistant, Tickets |
| `settings/` | One page per settings screen |
| `integrations/` | Phone/SMS, email, load boards, payments, the lead source API and MCP |
| `support/` | Contact details and troubleshooting |
| `images/app/`, `images/settings/` | Product screenshots, captured from the real app |
| `docs.json` | Navigation, theme and redirects |

## Editing

Content is MDX. Every page needs frontmatter with a `title` and a `description`:

```mdx
---
title: "Page title"
description: "One sentence that says what the page is for."
---
```

Do **not** add an `# H1` at the top of a page — Mintlify renders the frontmatter `title` as the
heading, and a second one duplicates it.

Adding a page means creating the `.mdx` file **and** listing it under the right group in
`docs.json`. A page that is not in `docs.json` is not reachable.

If you move or rename a page, add a `redirects` entry in `docs.json` so existing links keep working.

## Preview locally

```bash
npm i -g mint
mint dev
```

Then open http://localhost:3000.

Check links before you push:

```bash
mint broken-links
```

## Screenshots

Screenshots are captured at 1600×1000 with a 2× device scale factor, in light mode, using demo data
— never a real customer's account. Keep them consistent: same viewport, same theme, no personal
information.

Annotated screenshots (arrows and callouts) live alongside the plain ones with an `-annotated`
suffix.

## Publishing

Changes on the default branch deploy automatically through the Mintlify GitHub app.

## Keeping it accurate

When the product changes, the pages that most often need updating are:

- `settings/integrations.mdx` — when a provider is added or removed
- `settings/templates.mdx` — when a template event is added
- `get-started/lead-journey.mdx` and `using/shipments.mdx` — when a status or sub-filter changes
- `get-started/tour.mdx` — when the sidebar changes
