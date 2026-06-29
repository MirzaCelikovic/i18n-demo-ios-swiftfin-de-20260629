# i18n demo — Swiftfin (iOS) English→German

Forge demo output from the **Supergrow translation skill**: an agent enters an OSS app's codebase, machine-translates a slice of its English base catalog into a target locale, and opens a reviewable PR.

- **Gold app:** [jellyfin/Swiftfin](https://github.com/jellyfin/Swiftfin) (iOS)
- **Format:** legacy `.lproj/Localizable.strings` (`"key" = "value";`), `%@` / `%lld` placeholders
- **Target locale:** German (`de`)
- **Slice:** 209 keys (representative slice, not a full app translation)

## The PR

`main` holds the English base catalog (`Translations/en.lproj/Localizable.strings`). The branch `add-german-de` adds the generated German catalog (`Translations/de.lproj/Localizable.strings`), so the PR diff is exactly the new locale file.

## Forge result

- **Gate score:** 93→91/100 (reached plateau)
- **Mechanics verified:** `--all` → exit 0 (key parity + `%@` / `%lld` placeholder parity between `en` and `de`)

## What the worker learned

- Hold one German register (du/Sie) consistently across the whole table
- Native German typography: „…“

## Encoding note

The real Swiftfin app ships these `.strings` files as **UTF-16LE**. This demo file is committed as **UTF-8** for diff readability on GitHub.
