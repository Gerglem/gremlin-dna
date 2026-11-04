# Release notes

Download filenames carry no version, so the links in guides and forum posts keep
working. This file is how you tell what you actually have.

## Gremlin: Color Themes — current release v2.5.07

The build shipped as `gremlin-theme.ecigtheme` and `gremlin-full-setup.ecig`.

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
