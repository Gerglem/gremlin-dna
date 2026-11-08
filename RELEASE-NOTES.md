# Release notes

## Versions, and the build number

**A release is `major.minor`** — v2.5. That is what the download is called, what the
release is tagged, and what this file and the README call it.

**The last delimiter is a build number**, as in `v2.5.07`. It is tracked, it is real,
and it is deliberately not what the release is called:

> "Use the last delimiter like a build number. Published versions don't display them,
> but are included in the version number in the theme."

So the build is not displayed in the release — but it **is** in the theme, and there are
exactly two places to read it:

1. **The theme's own description** — `<Comments>` in an `.ecigtheme`,
   `EvolvThemeComments` in an `.ecig`. It reads `Gremlin - Color Themes v2.5.07`.
   This is the one place the build survives the file being renamed.
2. **The INFO screen's `Theme` row on the mod**, from build **v2.5.09 onward**. Builds
   up to and including v2.5.07 do not have that row.

**Those two must agree.** They are the same string from the same build, and if they ever
disagree the build is mislabeled. See
[which version do I have?](README.md#which-version-do-i-have).

### How the files are named

Every release ships the same artifact under two names, and both are real files. The
versioned name carries the **release**, `v2.5` — never the build.

| Name | Changes? | Use it for |
|---|---|---|
| `gremlin_vX.Y_theme.ecigtheme` | **Never.** Published once and frozen | Knowing which release you have. Rolling back. For a bug report, read the build out of the file as well |
| `gremlin_current_theme.ecigtheme` | **Every release** | Links in guides and forum posts, where you want the newest build without editing the link |
| `gremlin-theme.ecigtheme` | Every release | Nothing new — the original version-less name, kept because posts already link at it. It behaves exactly like `current` |

`current` is a copy rather than a symlink because GitHub cannot serve a git symlink as
a usable raw download. The files are under 50 KB, so the duplication is not worth
removing — and removing it would break links that already exist.

The profiles in `files/profiles/` and the TCR curves in `files/materials/` are **not
versioned**: the EScribe profile format has no field for a version, and the TCR curves
are material data. They are revised in place, and a tagged release is the way to pin
a whole known-good set.

### A note on the `v2.5.07` tag

**The convention above applies from the next release onward.** The published GitHub
release is tagged **`v2.5.07`** — a full version including the build — because it went
out before this was settled. It is a historical tag and it stays exactly as it is:
retagging or deleting a published release breaks every download URL already in the
wild. Its assets are named with the build too. Nothing after it will be.

### Promoting a new release

Copy the verified build into `files/` under its versioned names — **release only, no
build number in the filename** — then run this from the repo root. It is the whole
mechanical step; the stable names are only ever copies of the versioned file, so there
is nothing to decide:

```powershell
$r = "2.6"      # the release: major.minor, no build number
Copy-Item "files\gremlin_v${r}_theme.ecigtheme" "files\gremlin_current_theme.ecigtheme" -Force
Copy-Item "files\gremlin_v${r}_theme.ecigtheme" "files\gremlin-theme.ecigtheme"         -Force
```

Then bump the release in this file and in `README.md`, add the release entry below, and
tag the release **`v$r`** — `v2.6`, not `v2.6.03`. Record the build in the entry text,
where it belongs. The previous versioned files stay exactly where they are — nothing is
deleted and nothing is renamed, so every link that ever worked keeps working.

## Gremlin: Color Themes — current release v2.5

Shipped as `gremlin_v2.5_theme.ecigtheme`, and as the `current` and version-less copies
of it. **The combined `.ecig` was withdrawn 2026-11-07 — see the note at the top of
`README.md`.** The build inside these files is **v2.5.07**.

The entries below are **builds** — the history inside release v2.5.

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

- ~~Session time differs between the standalone profile files and the full-setup config.~~
  Moot since 2026-11-07: the full-setup config was withdrawn, so the standalone profiles
  are the only source and there is nothing left to disagree with.
  Being reconciled; set it to what you want on the mod in the meantime.
