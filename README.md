# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for B3dmar's Astro sites.

Keeps the whole fleet's dependencies — especially the **Astro toolchain** — moving
together and low-noise, so version bumps (Astro in particular) are one grouped PR
per repo instead of a hand-sync chore.

## Usage

Add a `renovate.json` to a repo:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>B3dmar/renovate-config"]
}
```

Then make sure the [Renovate GitHub App](https://github.com/apps/renovate) is
installed on the `B3dmar` org for that repo.

## What the preset does

- Extends `config:recommended`.
- **Groups `astro` + `@astrojs/*` + `astro-og-canvas` + fontsource fonts into one
  "astro ecosystem" PR** — they are coupled, so bumping them together avoids the
  partial-upgrade breakage that a lone `astro` bump would cause.
- **Holds Astro/adapter majors** behind the Dependency Dashboard for a deliberate,
  reviewed upgrade (minors and patches flow automatically).
- Weekly schedule (Mon before 9am, Europe/Copenhagen) + weekly lockfile maintenance.
- No automerge — every update is a PR you review and merge. Enable automerge later
  per repo if you want patch/minor to self-merge on green CI.
