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

Everything is in **[`files/`](files/)**. The filenames do not carry versions, so
these links always point at the current release.

| File | What it does |
|---|---|
| [`gremlin-full-setup.ecig`](files/gremlin-full-setup.ecig) | Theme **plus** the four profiles and both TCR curves. **Replaces every setting on the mod.** |
| [`gremlin-theme.ecigtheme`](files/gremlin-theme.ecigtheme) | The theme only. Keeps your profiles and settings. |
| [`files/profiles/`](files/profiles/) | The four profiles individually: V5 XL, Quest, and a burn-off for each |
| [`files/materials/`](files/materials/) | TCR curves — `dtv5xl-tcr200.csv` and `questcup-tcr125.csv` |

**Back up your own setup first** — in EScribe, `File -> Save`.

What changed, and which version you have: [`RELEASE-NOTES.md`](RELEASE-NOTES.md).

## Installing

All three paths go through EScribe over USB. **Back up what you have first:
`File -> Save`.** Nothing here is reversible from the mod itself.

1. Connect the mod by USB and open EScribe. It should say it is connected before you
   go further; if it does not, try a different cable, since plenty of USB-C cables are
   charge-only.
2. Pick one:
   - **Full setup** (easiest, replaces everything): `File -> Open` the `.ecig`, then
     **Upload Settings to Device**.
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
