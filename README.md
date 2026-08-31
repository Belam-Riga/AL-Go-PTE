# Belam-Riga AL-Go template

This is Belam-Riga's fork of Microsoft's [AL-Go-PTE](https://github.com/microsoft/AL-Go-PTE)
template. Our BC extensions (`blm_registers`, `blm_tools`, `blm_lursoft`,
`blm_vat_advance_payments`) sync their CI/CD workflow files from here, via `templateUrl` in
each repo's `.github/AL-Go-Settings.json`. Update this fork (and run each app repo's
"Update AL-Go System Files" workflow) instead of hand-editing each app repo's `.github`
folder individually.

## Versioning convention

Each app's `app.json` version has 4 numbers: `Major.Minor.Build.Revision` (e.g. `1.10.2.0`).

- **Major.Minor.Build** (the first 3 numbers, e.g. `1.10.2`) is what you control. Bump the
  **Build** number (3rd segment) for each release you want to ship. This is the number that
  matters — what goes in the changelog, what you compare between sandbox and production,
  what to ask about before changing.
- **Revision** (4th number) is no longer meaningful for what actually gets deployed to
  production: AL-Go automatically overwrites it with the GitHub Actions run number on every
  CI build, regardless of what's committed in `app.json`. Locally in VS Code, the 4th number
  still shows exactly what you typed (local Publish doesn't go through AL-Go) — fine to use
  for your own scratch tracking while iterating, just don't expect it to carry through to
  what ends up live in `Belam_live`.
- To confirm sandbox and production are running the same release, compare **Major.Minor.Build
  only** (e.g. "1.10.2") — guaranteed identical, since it only changes when someone
  deliberately bumps it. To know the *exact* commit behind a specific production deploy,
  check that deploy's GitHub Actions run log — it always shows the exact commit SHA.
- **Never bump an `app.json` version without asking Dmitrijs first.** That hasn't changed —
  only which digit moves has.

This is AL-Go's `versioningStrategy: 3` ("Build from app.json, Revision from the GitHub run
number") — a standard, Microsoft-documented built-in option, not a Belam-Riga-specific hack.

---

Below is Microsoft's original template README.

# AL-Go Per Tenant Extension Template

This template repository can be used for managing Per-tenant Extensions (PTEs) for Business Central.

Please go to https://aka.ms/AL-Go to learn more.

## Contributing

Please read [this](https://github.com/microsoft/AL-Go/blob/main/Scenarios/Contribute.md) description on how to contribute to AL-Go for GitHub.

We do not accept Pull Requests on the template repository directly.
