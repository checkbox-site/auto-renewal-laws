# US subscription auto-renewal laws: an open dataset

The requirements that US federal, state, District of Columbia and New York City automatic-renewal and negative-option
laws place on subscription businesses — the sign-up disclosure and consent, the acknowledgment, reminder notices and
their timing windows, online cancellation and record keeping — as structured data with a citation, a link to the
primary source and an effective date for every requirement.

Maintained by [Checkbox](https://checkbox.site) (a System1 company), which uses the same data to check subscription
checkouts. Browse it as web pages at https://checkbox.site/laws (one page per jurisdiction) and
https://checkbox.site/laws/data.

> **Not legal advice.** Every requirement is drafted from the cited primary source and is **pending attorney
> review** (`legal_review_status`). Laws change; check `last_reviewed` and the source before relying on an entry.

## Files

| File | What |
|---|---|
| [`data/laws.json`](data/laws.json) | Everything: metadata, jurisdictions with their laws, amendments and enforcement, and every requirement |
| [`data/requirements.csv`](data/requirements.csv) | One row per requirement (flattened `applies_when`, `notice_window` and `exposure`) |
| [`data/VERSION`](data/VERSION) | Catalog version of this snapshot (also `version` in `laws.json`) |

The same files are served at https://checkbox.site/laws/data.json and https://checkbox.site/laws/data.csv. This
repository is a versioned mirror, updated whenever the catalog changes; each update is a commit and a tag named after
the version.

## Fields (requirements)

`id` (stable, e.g. `US-CA.17602.a.3`), `jurisdiction`, `jurisdiction_name`, `law`, `stage` (signup, confirmation,
reminder, cancellation, records …), `title`, `summary`, `citation`, `source_url`, `effective_date`, `sunset_date`,
`applies_when` (free trial, trial length, term length, online sign-up, consumer only, payment methods),
`notice_window` (min / max days before or after an anchor such as the trial end or renewal), `severity`, `exposure`
(private right of action, remedies, damages, cure period), `check_ids` (the Checkbox checks that test it),
`legal_review_status`, `url` (the jurisdiction's web page).

## Use and cite

License: [CC BY 4.0](LICENSE). Attribution: name Checkbox, link to https://checkbox.site/laws/data, give the version,
and say whether you changed the data — for example:

> Checkbox, US Subscription Auto-Renewal Requirements Dataset, version 2026.11.01.1, https://checkbox.site/laws/data (CC BY 4.0)

(use the version in `data/VERSION`). See [CITATION.cff](CITATION.cff).

```python
import pandas as pd
reqs = pd.read_csv("https://raw.githubusercontent.com/checkbox-site/auto-renewal-laws/main/data/requirements.csv")
reqs[reqs.stage == "cancellation"][["jurisdiction", "citation", "title"]]
```

## Report an error

Open an issue with the requirement `id`, what is wrong and a link to the primary source (statute, regulation or
official guidance). See [CONTRIBUTING.md](CONTRIBUTING.md).
