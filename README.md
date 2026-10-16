# presence

The public presence artifact for Gearóid Ó Treasaigh: the values his websites
render, published as one pinned, fetchable thing.

**Everything here is generated. Do not edit it.** Changes made in this
repository will be overwritten by the next publish and will not reach the source
of truth. The source is a private repository; this is an export from it,
containing only what has been explicitly cleared to publish.

## What is in it

| File | What it is |
|---|---|
| `presence.json` | Identity values, prose blocks, and the career record's public-facing entries |
| `gearoid.webp` | The canonical headshot, travelling beside the JSON so one fetch gives a consumer everything |

`presence.json` carries `identity` (name, location, links, headshot filename),
`blocks` (short bio, services, skills, and the engagement summary), and the
structured record: `experience`, `projects`, `awards`, `certifications`,
`education`. Every value is present because it was individually classified for
publication. Anything not classified is absent by default.

## How to consume it

**Pin an exact tag or commit SHA. Never track a branch tip.**

A build must produce the same site tomorrow as it does today from the same
commit, and a moving dependency quietly breaks that. Fetch a tag, not `main`.

```bash
curl -fsSL -o data/presence.json \
  https://raw.githubusercontent.com/<owner>/presence/<tag>/presence.json
```

`-f` matters: a fetch failure must fail the build loudly rather than deploying a
site with stale or missing data.

### Two things the schema asks of you

**`experience` is two-level, not flat.** Each entry carries a `via` field
holding the id of the entry whose employer made it possible, or `""` for a
directly held role. Group by employer and follow `via` to render the nesting.
Rendering the array flat produces one company appearing several times as
separate concurrent jobs, which is wrong and looks like a bug.

**`headshot_path` is a bare filename**, resolving against this repository, not a
path into anything. Derive your own sizes from it; it is deliberately not
pre-sized, because sizing is presentation and presentation belongs to the site.

## What is deliberately not here

Contact details beyond the published links, anything from the private record,
and any value that has not been individually cleared. An absent field is a
decision, not an oversight.
