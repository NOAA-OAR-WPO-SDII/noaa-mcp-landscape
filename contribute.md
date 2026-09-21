---
layout: doc
title: Add or update an entry
summary: Two ways to contribute — a short web form, or a pull request adding one file.
permalink: /docs/contribute/
---

Every entry in the registry is a single file in `_projects/`. Adding or
correcting an entry means adding or editing one file — nothing else.

You don't need to know anything is "true" before submitting. A concept with two
filled-in fields is a useful entry; the point is to make experimentation
visible and reduce duplicated effort.

## Option 1 — Submit the web form (easiest)

Open a **New entry** issue and fill in the fields. A maintainer converts it into
an entry file and adds it. This needs only a GitHub account.

> **[Open the “New entry” form →]({{ site.repo_url }}/issues/new?template=new_entry.yml)**

Use the **Update / correct an entry** form the same way to flag anything stale
or wrong, including the point of contact or the `last_verified` date.

## Option 2 — Open a pull request (add the file yourself)

1. Copy `PROJECT_TEMPLATE.md` to `_projects/<your-entry-id>.md`.
2. Fill in the fields (reference below), keeping the surrounding `---` fence lines.
3. Open a pull request.

The **filename is the entry's permanent id** and becomes its URL:
`_projects/erddap-mcp.md` is served at `/project/erddap-mcp/`. Use lowercase
words separated by hyphens, and keep it stable once merged so links don't break.

> Entry files are Markdown with a YAML "front matter" block — the part between
> the `---` lines. That's where all the fields go; the body below can stay
> empty. The fences are what tell the site to publish the file as its own page.

## Field reference

| Field | Required | Notes |
|---|---|---|
| `name` | yes | Display name of the project. |
| `organization` | yes | Owning org(s), e.g. `NOAA / Noblis`. Used as a filter. |
| `affiliation` | yes | `NOAA` or `External` — whether the effort is internal to NOAA or a third party. Used as a filter. |
| `poc` | recommended | Point of contact: `{ name, role, email }`. Shown on the entry page. |
| `summary` | yes | One sentence for the registry card. |
| `status` | yes | One of the status values below. |
| `mcp_type` | yes | One of the MCP-type values below. |
| `resource` | yes | One of the resource values below. |
| `overview` | recommended | A short paragraph — what it is and why. |
| `capabilities` | recommended | List of what the MCP interface can do. |
| `resources_exposed` | recommended | List of data / documents / tools it exposes. |
| `architecture` | optional | Server framework, transport, hosting, auth. |
| `status_detail` | optional | A sentence on how far along it is. |
| `evidence` | optional | List of `{ label, url }` links: repos, docs, demos. |
| `last_verified` | yes | `YYYY-MM-DD` — when someone last confirmed this. |

`poc` can also be a plain string (e.g. `poc: Jane Doe, jane.doe@noaa.gov`) if you
don't want the structured form. If there's no known owner, use `TBD`.

### Controlled vocabularies

Keep these to the listed values so the filters stay clean. Propose new values in
an issue if something genuinely doesn't fit.

**status** — `concept` · `prototype` · `pilot` · `production` · `archived`

**mcp_type** — `server` · `client` · `host` · `both`
(A *server* exposes resources/tools over MCP. A *client* / *host* consumes MCP
servers. Use `both` only when one project genuinely does each.)

**resource** — `data access` · `knowledge management` · `tooling` · `workflow` ·
`modeling` · `other`

**affiliation** — `NOAA` · `External`
(Use `NOAA` for efforts run by NOAA offices, labs, programs, or NOAA-funded
contractors and cooperative institutes acting on NOAA's behalf. Use `External`
for independent third-party projects, even when they build on NOAA data.)

See [Terminology](../terminology/) for definitions.

## Template

Copy this into `_projects/<id>.md`, keeping the `---` lines:

```yaml
---
name: Example MCP Project
organization: NOAA / Partner
affiliation: NOAA        # NOAA | External
poc:
  name: Jane Doe
  role: Maintainer
  email: jane.doe@example.org
summary: >-
  One sentence describing what this exposes or does.

status: prototype        # concept | prototype | pilot | production | archived
mcp_type: server         # server | client | host | both
resource: data access    # data access | knowledge management | tooling | workflow | modeling | other

overview: >
  A short paragraph: what it is, who it's for, and why it exists.

capabilities:
  - What the MCP interface can do
  - Another capability

resources_exposed:
  - A dataset, document set, or tool it exposes
  - Another resource

architecture: >
  Server framework, transport, hosting, and auth model.

status_detail: >
  One sentence on maturity and support level.

evidence:
  - label: Repository
    url: https://example.org/repo
  - label: Design doc
    url: https://example.org/doc

last_verified: 2026-09-01
---
```

## Review conventions

- Entries are community-contributed and may be incomplete — that's expected.
- Maintainers check that the vocabularies are respected and links resolve; they
  don't independently verify claims.
- If you can't find an owner, leave `poc` as `TBD` rather than guessing.
