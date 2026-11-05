# Release notes

## How the files are named

Every release ships the same artifact under two names, and both are real files.

| Name | Changes? | Use it for |
|---|---|---|
| `gremlin_vX.Y.ZZ_theme.ecigtheme`, `gremlin_vX.Y.ZZ.ecig` | **Never.** Published once and frozen | Knowing what you have. Reporting a bug against a build. Rolling back |
| `gremlin_current_theme.ecigtheme`, `gremlin_current.ecig` | **Every release** | Links in guides and forum posts, where you want the newest build without editing the link |
| `gremlin-theme.ecigtheme`, `gremlin-full-setup.ecig` | Every release | Nothing new — these are the original version-less names, kept because posts already link at them. They behave exactly like `current` |

The version is also **inside** every file, in the theme description
(`<Comments>` in an `.ecigtheme`, `EvolvThemeComments` in an `.ecig`), which is the
only place it survives being renamed. From **v2.5.09 onward** it is on the device too,
in the INFO screen's `Theme` row. See
[which version do I have?](README.md#which-version-do-i-have).

`current` is a copy rather than a symlink because GitHub cannot serve a git symlink as
a usable raw download. The files are under 50 KB, so the duplication is not worth
removing — and removing it would break links that already exist.

The profiles in `files/profiles/` and the TCR curves in `files/materials/` are **not
versioned**: the EScribe profile format has no field for a version, and the TCR curves
are material data. They are revised in place, and a versioned `.ecig` is the way to pin
a whole known-good set.

### Promoting a new release

Copy the verified build into `files/` under its versioned names, then run this from the
repo root. It is the whole mechanical step — the stable names are only ever copies of a
versioned file, so there is nothing to decide:

```powershell
$v = "2.5.10"   # the new version
Copy-Item "files\gremlin_v${v}_theme.ecigtheme" "files\gremlin_current_theme.ecigtheme" -Force
Copy-Item "files\gremlin_v${v}_theme.ecigtheme" "files\gremlin-theme.ecigtheme"         -Force
Copy-Item "files\gremlin_v${v}.ecig"            "files\gremlin_current.ecig"            -Force
Copy-Item "files\gremlin_v${v}.ecig"            "files\gremlin-full-setup.ecig"         -Force
```

Then bump the version in this file and in `README.md`, and add the release entry below.
The previous versioned files stay exactly where they are — nothing is deleted and
nothing is renamed, so every link that ever worked keeps working.

## Gremlin: Color Themes — current release v2.5.07

Shipped as `gremlin_v2.5.07_theme.ecigtheme` and `gremlin_v2.5.07.ecig`, and as the
`current` and version-less copies of both.

- **v2.5.07** — **removed `Set unlock` from the LOCK menu.** On a DNA100C that row starts a sequence that never completes, and while it waits it ignores every button press, so the mod looks dead until you recover it. It sat one row below `After`, where you could land on it by accident. Nothing else changed.
- **v2.5.06** — the live resistance is back on the home screen.
- **v2.5.05** — the screen stays lit longer.
- **v2.5.04** — the pulse icon goes with the number it labels.
- **v2.5.03** — the live resistance row only shows a live reading.
- **v2.5.00–v2.5.02** — six switchable color schemes under MENU → THEMES, an orange
  FIRING box, a red LOW BATTERY banner below 15%, and a profile-colored accent line.
- **v2.3.04** — Lightning Quest back to TCR 125.
- **v2.1–v2.3** — color themes introduced, menu text fixes for long values and names.
- **v1.0** — first release.

### What changed for this public release

- **Both vaping profiles start at 380°F.** Earlier files disagreed with each other: the
  standalone profiles said 380 and the full-setup config said 385. They now both say 380.
- **Lightning Quest ships TCR 125**, Divine Tribe's published figure. Some earlier files
  and guides said 120, from a single swab test on a single mod.
- **Cold resistance is cleared and unlocked in every file**, on purpose. See the warning
  in [`README.md`](README.md) — these are safe to distribute, not safe to fire until you
  lock your own.

## Gremlin High Contrast: Large Text

**Not published yet.** The newest builds have never been checked on a physical mod, and a
theme whose whole purpose is legibility should be looked at by eye before it goes to people
who depend on it. Coming once that check is done.

## Known

- `Pwr bank` is still listed on the LOCK menu and does nothing on a DNA100C — it
  will not take focus. Harmless, but it is a row that does not work.

- Session time differs between the standalone profile files and the full-setup config.
  Being reconciled; set it to what you want on the mod in the meantime.
