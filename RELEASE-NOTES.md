# Release notes

## Versions, and the build number

**A release is `major.minor`** — v2.9. That is what the download is called, what the
release is tagged, and what this file and the README call it.

**The last delimiter is a build number**, as in `v2.9.00`. It is tracked, it is real,
and it is deliberately not what the release is called:

> "Use the last delimiter like a build number. Published versions don't display them,
> but are included in the version number in the theme."

So the build is not displayed in the release — but it **is** in the theme, and there are
exactly two places to read it:

1. **The theme's own description** — `<Comments>` in an `.ecigtheme`,
   `EvolvThemeComments` in an `.ecig`. It reads `Gremlin v2.9.00` (`Gremlin - Color
   Themes v2.5.07` on the previous release).
   This is the one place the build survives the file being renamed.
2. **The INFO screen's `Theme` row on the mod**, from build **v2.5.09 onward**. Builds
   up to and including v2.5.07 do not have that row.

**Those two must agree.** They are the same string from the same build, and if they ever
disagree the build is mislabeled. See
[which version do I have?](README.md#which-version-do-i-have).

### How the files are named

Every Gremlin release ships the same artifact under two names, and both are real files.
The versioned name carries the **release**, `v2.9` — never the build.

| Name | Changes? | Use it for |
|---|---|---|
| `gremlin_vX.Y_theme.ecigtheme` | **Never.** Published once and frozen | Knowing which release you have. Rolling back. For a bug report, read the build out of the file as well |
| `gremlin_current_theme.ecigtheme` | **Every release** | Links in guides and forum posts, where you want the newest build without editing the link |
| `gremlin-theme.ecigtheme` | Every release | Nothing new — the original version-less name, kept because posts already link at it. It behaves exactly like `current` |

High Contrast and Lantern ship under their versioned names only, on their own version
tracks: `gremlin_high_contrast_vX.Y_theme.ecigtheme`, `lantern_vX.Y_theme.ecigtheme`, and
`lantern-<accent>_vX.Y_theme.ecigtheme` for each accent color.

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

## Gremlin — current release v2.9

Shipped as `gremlin_v2.9_theme.ecigtheme`, and as the `current` and version-less copies
of it. The build inside these files is **v2.9.02**. The previous release,
`gremlin_v2.5_theme.ecigtheme`, stays exactly where it was.

**v2.9.02:** the theme's description in EScribe now states chip support accurately: tested on a
DNA100C; expected to work on the DNA75C and DNA250C but not yet tested on them (testers welcome);
not for the DNA60C, DNA80C or non-color chips. The INFO screen's `Theme` row reads v2.9.02.
Nothing else changed.

**v2.9.01:** on the NEW COIL? screen, the red bar that flags a new coil past its replace threshold moved 2 pixels right, because the screen's two leftmost pixel columns do not show on the DNA 100C; NEW and OLD moved with it. Nothing else changed.

**The color schemes are gone.** Gremlin is function over form, so v2.9 has one look:
**text is white, and color only marks things** — red for a warning, orange for firing or
heat, yellow for charging. Colored text washes out in sunlight; a white number next to a
colored marker does not. MENU → THEMES is removed, and so are Synth, Desert, Terminal
and the rest. If you had one switched on, it simply has no effect any more.

What changed since v2.5, from your side of the screen:

- **One temperature, and it says which one it is.** At idle the big number is the
  setpoint, labeled `SET`, and you edit it in place. While firing it is the cup
  temperature, labeled `CUP`, inside an orange frame. On a cleaning profile, which runs on
  wattage, it is the board temperature, labeled `BOARD`.
- **While firing the screen quiets down:** the ohm-lock row hides and the session time
  goes gray, so the temperature and the chip's own status line are what you see.
- **Battery:** a small battery gauge and percentage replace the bar and the `LOW BATTERY`
  banner. The gauge outline turns red below 15% and yellow while charging.
- **Charging:** a bolt appears next to the battery, and the board temperature shows in the
  top right corner, only while charging. The bolt turns orange if the board goes above
  140°F.
- **Unlocked cup:** `NO LOCK` is white, with its row icon turning red.
- **PUFF screen:** MENU → INFO → `Last` opens a chart of your last puff — temperature and
  power over time, with its length, peak temperature and power. Step back through earlier
  puffs with `<` and `>`.
- **INFO** carries a `Theme` row with the full version, build included.
- **MENU → LOCK → After** steps in tens of minutes, and reads `Off` when auto-lock is off.
- In EScribe the theme is now called **Gremlin** rather than **Gremlin - Color Themes**.

## Gremlin: Color Themes — v2.5

Shipped as `gremlin_v2.5_theme.ecigtheme`. **The combined `.ecig` was withdrawn 2026-11-07 — see the note at the top of
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

## Lantern

**First public release: Lantern v1.6**, now build **v1.6.01**, and three accent colors of it:
Lantern Silver **v1.3** (build v1.3.01), Lantern Azure **v1.0** and Lantern Jade **v1.0**
(builds v1.0.01).

**Builds v1.6.01 / v1.3.01 / v1.0.01:** the description in EScribe states chip support accurately
(tested on a DNA100C; expected on the DNA75C and DNA250C, not yet tested; not for the DNA60C, DNA80C
or non-color chips), and the INFO screen shows the new build. Nothing else changed.

Lantern sits between the other two. A mod screen is glanced at, one-handed, often in poor
light, and it has to answer three things: what will this do, is anything wrong, and what is
happening right now. So the home screen has three fixed zones, one big number, and three
places you can press.

- **Text is white; color marks.** Orange means the coil is live, red means a fault. While
  firing nothing moves: the number and `CUP` stay white and the rules and a frame around
  them light up orange.
- **Coil warnings** — a cup past its replace point, or `NO LOCK` — keep white text,
  bracketed by two red bars.
- **Charging:** a bolt appears next to MENU, and the board temperature takes the session
  time's place until you unplug. The bolt turns red if the board goes above 140°F.
- **Menus:** Profile, Coil (resistance, lock, measure), Preheat, Screen (brightness,
  stealth, clock and more), Lock and Info.

| File | Accent |
|---|---|
| `lantern_v1.6_theme.ecigtheme` | white selection bar, gray rules |
| `lantern-silver_v1.3_theme.ecigtheme` | silver, plus a silver scale band on the lock screen |
| `lantern-azure_v1.0_theme.ecigtheme` | blue |
| `lantern-jade_v1.0_theme.ecigtheme` | green |

The four are the same screens. Only the selection bar, the thin rules and the charging
bolt change color, so pick by taste.

## Gremlin High Contrast: Large Text

**First public release: v1.3**, now build **v1.3.03**, shipped as
`gremlin_high_contrast_v1.3_theme.ecigtheme`.

**v1.3.03:** now fits the DNA 75C. The large-number font stored letters and symbols the screen never
draws; those are blanked, which frees enough space for the 75C. Every screen looks the same. The
description in EScribe states chip support accurately (tested on a DNA100C; expected on the DNA75C and
DNA250C, not yet tested; testers welcome).

Built from scratch for people who have trouble reading a mod screen: large text, white and
yellow on black, and only what is needed on each screen.

- **Home:** MENU and battery percentage across the top, the profile name, the temperature
  in large digits, the editable `SET` temperature, and the chip's status line.
- **While firing** the screen clears to `TEMP`, the live temperature in the big digits, and
  `FIRING` in an orange frame.
- **Warnings are carried by a bar, not by colored text:** a red bar under a coil that needs
  replacing or a low battery, an orange one when the board is hot.
- **Charging:** a bolt appears beside the battery number, and the large temperature
  gives way to the board temperature, labeled `BOARD`. Above 140°F it reads `BOARD HOT`.
- **Menu:** temperature, watts, brightness, and an `Ω OHMS` page with the locked resistance,
  the lock and MEASURE.

## Known

- `Pwr bank` is still listed on the LOCK menu and does nothing on a DNA100C — it
  will not take focus. Harmless, but it is a row that does not work.

- ~~Session time differs between the standalone profile files and the full-setup config.~~
  Moot since 2026-11-07: the full-setup config was withdrawn, so the standalone profiles
  are the only source and there is nothing left to disagree with.
  Being reconciled; set it to what you want on the mod in the meantime.
