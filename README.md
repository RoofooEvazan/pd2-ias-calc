# PD2 Attack Speed

An attack speed calculator for **Project Diablo 2**. Every number comes from the game's own code and PD2's data files, not from community formulas.

**Live site:** https://roofooevazan.github.io/pd2-ias-calc/

## What's on the site

| Tab | What it does |
|---|---|
| **IAS Calculator** | Frames per attack and breakpoints for any class, form (human, werewolf, werebear), weapon, attack and skill. Sequence skills show when each hit lands; in werewolf / werebear form, Rabies and Hunger (S3) are covered, and the notes say how much IAS the weapon itself needs and how much in total. Includes a grid of weapon IAS × other-gear IAS. |
| **Fastest Frames** | For every class and form, the two fastest held-attack frame counts and every weapon setup that reaches them. Click a class, form or frame count to expand it. Each row has an **Open** button that loads it into the calculator. |
| **How IAS is Calculated** | A plain-language, step-by-step explanation for human, werewolf and werebear, with worked examples. |
| **Developer Reference** | The full rules, data formats, extracted tables, a reference implementation and a map of the game functions behind them. |

It works on desktop and mobile. The whole site is one file (`index.html`) with no server, build step or tracking.

## How the numbers were established

The rules were recovered from the Diablo II 1.13c DLLs that PD2 uses (`D2Common.dll`, `D2Game.dll`, `D2Client.dll`), with PD2's own changes from `ProjectDiablo.dll` applied. Animation and item data come from PD2's `data.zip`.

Most rules were **verified**. The game's own machine code was loaded into a test harness and run directly on the CPU with tens of thousands of inputs, and it matched the formulas on every case. The few rules that were only read from the code, not run, are marked **READ** in the Developer Reference. The full research log is in [`FINDINGS.md`](FINDINGS.md).

In werewolf / werebear form, the speed step uses the human attack named by the weapon's own class in the item data, so two-handed swords count as the one-hand swing (corrected 2026-10-07, verified natively and in-game: a werewolf Barbarian with a Colossal Sword holds at 4 frames with 140 weapon IAS, not 5; see `FINDINGS.md`).

## Updating the site

Replace `index.html` with a new version, then commit. GitHub Pages republishes automatically within a minute or two.

## Disclaimer

This is a fan-made tool. It is not affiliated with or endorsed by Blizzard Entertainment or the Project Diablo 2 team. Diablo is a trademark of Blizzard Entertainment. All artwork on the site is original and drawn in code; no game assets are included.
