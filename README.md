# Gremlin — custom themes for Evolv DNA color mods

Two themes for **Evolv DNA75C / DNA100C / DNA250C** chips, plus Divine Tribe
profiles and swab-calibrated TCR curves for the **V5 XL** and **Lightning Quest**
cups. Free, and the files here are the ones I run.

| Theme | For | Guide |
|---|---|---|
| **Gremlin: Color Themes** | Live temperature, home-screen editing, battery bar, six switchable color schemes | [setup and calibration](setup-gremlin-theme-profiles-calibration.md) |
| **Gremlin High Contrast: Large Text** | Built from scratch for people who have trouble reading a mod screen | **not published yet** - see [`RELEASE-NOTES.md`](RELEASE-NOTES.md) |

Swapping a DNA100C into a Lost Vape Thelema Solo is a separate guide:
**[chip swap](chip-swap-thelema-solo-dna100c.md)**.

## Requirements

- A **DNA color chip** — DNA75C, DNA100C or DNA250C. Not for non-color DNA chips; DNA60C untested.
- **Evolv's international firmware**, if you want Session Mode (DNA autofire). The US firmware does not have it.
- **EScribe**, Evolv's free software: <https://www.evolvapor.com/escribe>
- Up, select and down buttons plus fire.

## Downloads

Everything is in **[`files/`](files/)**. The current release is **v2.5**.

**If you just want the thing, take a `current` file.** It is always the newest
release, so a link to it keeps working.

| File | What it does |
|---|---|
| [`gremlin_current_theme.ecigtheme`](files/gremlin_current_theme.ecigtheme) | The theme only. Keeps your profiles and settings. |
| [`files/profiles/`](files/profiles/) | The four profiles individually: V5 XL, Quest, and a burn-off for each |
| [`files/materials/`](files/materials/) | TCR curves — `dtv5xl-tcr200.csv` and `questcup-tcr125.csv` |

**If you want a specific release — or want the file still to make sense in your
Downloads folder next year — take the versioned one.** A versioned file never
changes once it is published:

| File | |
|---|---|
| [`gremlin_v2.5_theme.ecigtheme`](files/gremlin_v2.5_theme.ecigtheme) | theme only, v2.5 |

One older name, [`gremlin-theme.ecigtheme`](files/gremlin-theme.ecigtheme), is still
here and still tracks the current release. Forum posts link straight at it, so it is
not going away — but new links should use `current` or a version.

> ### The combined `.ecig` files were withdrawn on 2026-11-07
>
> `gremlin_current.ecig`, `gremlin_v2.5.ecig` and `gremlin-full-setup.ecig` are gone,
> and **an old link to one of them will 404.** That is deliberate.
>
> They carried **Max USB Charge Rate = 3.0 A**. Loading a config does not merge — it
> writes *every* setting the board has, so anyone who had deliberately set a slower
> charge rate for their own cells would have been put back to 3 A **without being told
> and without having asked**. Leaving the setting out of the file would not have helped:
> an omitted setting is written as its default, and the default is 3 A.
>
> **Nothing is lost.** The theme, the four profiles and both TCR curves are all still
> here as separate files, and the
> [setup guide](setup-gremlin-theme-profiles-calibration.md) walks through loading them —
> it is a few more clicks and it leaves your own battery settings alone.
>
> A corrected combined file may return once it ships the safer rate deliberately rather
> than inheriting one.

**Back up your own setup first** — in EScribe, `File -> Save`.

> **The `current` files are copies, not links, and that is on purpose.** GitHub cannot
> serve a git symlink as a usable raw download, so `current` has to be a real copy of
> the newest versioned file — right now it is byte-for-byte the same as `v2.5`. These
> files are under 50 KB each. The duplication is cheaper than breaking every link that
> is already out in the wild, so please don't "fix" it.

### Which version do I have?

The release is called **v2.5**. Inside the theme there is a third number — the build,
as in `v2.5.07`. It is not part of what the release is called, and you do not need it
unless you are reporting a bug or comparing two builds. Two places will tell you:

- **In EScribe** — load the file and read the theme's description: the **Theme** tab for
  an `.ecigtheme`, **Mod → Theme** for an `.ecig`. It starts with
  `Gremlin - Color Themes v2.5.07` — release *and* build. This works for every build ever
  shipped, including files you downloaded before the filenames carried versions.
- **On the mod** — from build **v2.5.09 onward** the INFO screen carries a `Theme` row
  showing the full version, build included, so you can check a mod you did not set up
  yourself. **Build v2.5.07 and earlier do not have that row**, so for the current
  release use EScribe.

The two always agree: the INFO row and the theme description are the same string from
the same build.

**The filename only ever carries the release**, `v2.5`, never the build — and `current`
and the two older names carry no version at all. If you need to know the build, read it
out of the file or off the mod.

The profiles and the TCR curves carry **no version at all**. The EScribe profile format
has nowhere to put one, and the TCR curves are material data rather than a build, so
both are revised in place. If you need a known-good theme-and-profile combination, take
**the files from a single tagged release** — everything published under one tag was built
and checked together.

What changed in each release: [`RELEASE-NOTES.md`](RELEASE-NOTES.md).

## Installing

Both paths go through EScribe over USB. **Back up what you have first:
`File -> Save`.** Nothing here is reversible from the mod itself.

1. Connect the mod by USB and open EScribe. It should say it is connected before you
   go further; if it does not, try a different cable, since plenty of USB-C cables are
   charge-only.
2. Pick one:
   - **Theme only** (keeps your profiles): **Theme** tab, load the `.ecigtheme`, then
     **Upload Settings to Device**.
   - **A single profile**: **General** tab, pick an empty profile slot, **Load Profile**,
     choose the `.ecigprofile`, then **Upload Settings to Device**. The profile carries
     its own TCR curve, so you do not need to import the `.csv` separately.
3. **Lock your cold resistance. Do not skip this.** With the cup attached and at room
   temperature: **General** tab, **Measure Ohms**, tick **Locked**, then upload again.
   Every file here ships with this cleared, so until you do it the mod has no reference
   and temperature control will not behave.
4. **Run a swab test before you trust the number** — see
   [the calibration guide](setup-gremlin-theme-profiles-calibration.md#4-calibrate-with-a-swab-test-do-this-every-mod-reads-a-little-differently).
   Briefly: set 470 degF, fire, wait for the temperature to stop climbing, hold a cotton
   swab on the floor of the cup about 10 seconds, and read the color. Light gold is
   roughly on target; dark brown means your mod runs hot and the TCR needs lowering.

If the mod locks itself after an upload, that is normal. Unlock it with five clicks of
the fire button.

## Two things that will bite you

**A file from here ships with no reference resistance.** Cold ohms are cleared and
unlocked on purpose, so you are not running my cup's measurement. That makes these
files safe to hand around and **not** safe to fire until you lock your own: with the
cup at room temperature, `General → Measure Ohms`, tick **Locked**, upload. A reading
taken on a warm cup makes the mod run hot.

**Every mod and every cup reads a little differently.** Do a swab test before you
trust the temperature. Start low and work up.

## Feedback

Issues and questions are welcome — open an issue here, or reply in the
r/DivineTribeVaporizers thread. Telling me your chip, firmware edition and cup is
most of the diagnosis.

Soldering lithium battery leads is at your own risk.
