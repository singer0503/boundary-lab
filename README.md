[English] | [繁體中文](README.zh-TW.md)

# Boundary Lab

> Boundary asymmetry × field coupling × quantum vacuum — an open, hobbyist precision-measurement log on propellantless propulsion and gravity-coupling phenomena (often labelled "antigravity" in popular discourse).

This is a passion project, not a startup. A single salaried researcher in his evenings and weekends, working with Claude Opus as a long-term collaborator, trying to do honest precision measurements on a class of physical claims that the mainstream has mostly stopped looking at.

We probably won't discover antigravity. But if we do the measurements carefully enough, we can at least say *"no, we didn't find it"* with high confidence — and in this field, that is already a contribution.

---

## What this repo is

A reproducible, openly-licensed lab notebook tracking experiments on:

- Townsend Brown's asymmetric capacitor effect (Biefeld–Brown)
- Podkletnov's rotating superconductor gravity-shielding claim
- Buhler / Exodus Propulsion's electrostatic-pressure thrust claim
- McCulloch's Quantized Inertia (QI) framework
- Fetisov 2022's room-temperature YBCO + RF weight-loss replication

Our working hypothesis (**a hypothesis, not a conclusion**): if any of the above are real, they may share a common underlying mechanism — *boundary asymmetry + field coupling + quantum vacuum*.

## What this repo is NOT

To save everyone time:

- ❌ Not a project that claims to have discovered antigravity.
- ❌ Not a fundraiser, business plan, or token project.
- ❌ Not a conspiracy, free-energy, or perpetual-motion platform.
- ❌ Not a guarantee of results — most outcomes here will be null or inconclusive.
- ✅ A public log of carefully designed measurement experiments.
- ✅ A platform that welcomes independent replication, criticism, and falsification.

## Who this is for

Come build with us if:

1. **You enjoy precision measurement** — fighting thermal drift, characterising noise floors, the small joy of a clean PSD plot.
2. **You'll share your negative results** — *"I tried X and saw nothing"* is data we want.
3. **You don't expect this repo to make anyone rich** — there's no exit. The reward is the work, and the people you do it with.

If those three sound right, you're in the right place.

## Why open source

The relevant research from the last seventy years (Brown, Podkletnov, Grebennikov, Hayasaka, Ning Li, Woodward...) has a structural problem: closed data, hard-to-reproduce experiments, and high career risk. Most of those researchers ended up at small private outfits or lost mainstream funding entirely. We think the field's progress has been badly slowed by that.

Publishing every protocol, raw dataset, analysis script, and failure log is, we believe, the only path forward. Even if every experiment we run returns zero, those zeros have scientific value — Tajmar et al's 2021 falsification of the EmDrive is some of the most important work this field has seen in years.

## Scientific discipline (the 8 non-negotiable rules)

Every experiment and release in this repo is bound by these:

1. **No exaggeration.** Words like *"breakthrough"*, *"success"*, *"verified"* do not appear in titles, abstracts, commit messages, or social posts unless an independent third party has replicated the work.
2. **Null results published equally.** Failures, no-effects, and inconclusive results get the same format and priority as positive findings.
3. **Raw data is immutable.** Files in `data/raw/` are append-only. All processing happens in `analysis/` and reproduces from raw.
4. **Method before result.** Every experiment's SOP must be committed to `protocols/` and `git tag`-frozen before execution. Post-hoc edits don't count as the original SOP.
5. **Every claim cites.** Scientific claims need a citation or a raw-data link. AI-generated synthesis is labelled and reviewed under the same standard.
6. **Errors first.** Every measurement carries a quantified uncertainty, noise floor, and systematic-error discussion. A number without an error bar is not a scientific datum.
7. **Independently reproducible.** Hardware BOM, wiring diagrams, calibration logs all live in `hardware/` and must let another researcher rebuild from scratch.
8. **AI collaboration is transparent.** Claude Opus is a long-term collaborator on this repo. Its specific contributions to experiment design, literature review, and analysis are tracked in `AI_CONTRIBUTIONS.md`.

Anything that violates any of these gets rolled back, corrected, or publicly retracted.

## Safety (read this twice)

Some experiments here involve genuinely lethal risks. Before doing any of them:

- **High voltage (>1 kV):** insulating gloves, insulating mat, single-hand rule, second person present, e-stop within reach.
- **Liquid nitrogen:** ventilated space only, eye protection, cryo gloves; asphyxiation risk in enclosed rooms.
- **Strong magnets (N42+):** pinch and projectile hazards; keep away from pacemakers and magnetic media.
- **Vacuum chambers:** use rated vessels only — *not* household glass; implosion risk.
- **Capacitors:** high-voltage caps can hold lethal charge after disconnection; always short to ground via a discharge stick first.

Anything in this repo is **for research reference only**. If you replicate any of it, you accept full responsibility for your own safety. The maintainer accepts no legal liability for any harm arising from replication.

## Repository structure

```
boundary-lab/
├── README.md             # this file (English)
├── README.zh-TW.md       # 繁體中文版本
├── NAMING.md             # how this repo got its name (and ◯)
├── NAMING.zh-TW.md       # 命名故事
├── LICENSE               # MIT (source code)
├── LICENSE-DOCS          # CC BY 4.0 (documentation)
├── LICENSE-DATA          # CC0 1.0 (raw experimental data)
├── LICENSING.md          # explainer for the three-tier licensing
├── CLAUDE.md             # operating rules for the AI collaborator
├── AI_CONTRIBUTIONS.md   # log of specific AI contributions (TBD)
├── SAFETY.md             # detailed safety procedures
├── SAFETY.zh-TW.md       # 安全規範
├── CONTRIBUTING.md       # how to join us
├── CONTRIBUTING.zh-TW.md # 加入我們
├── docs/                 # design proposals (e.g., propulsion-bench)
├── protocols/            # versioned SOPs, one folder per experiment
│   └── <experiment-id>/  # protocol, expected results, stop conditions
├── data/
│   ├── raw/              # raw data, append-only, never modified
│   └── processed/        # derived data (regeneratable from raw)
├── analysis/             # Python / Jupyter scripts
├── hardware/             # BOM, wiring diagrams, calibration logs, CAD files
├── papers/               # cited literature PDFs + reading notes
├── reports/              # public stage reports (including null results)
└── retracted/            # withdrawn/corrected content (never deleted; public record)
```

## Roadmap (tentative)

Currently in **Phase 0 — measurement baseline establishment**.

| Phase | Goal | Est. cost (USD) | Status |
|-------|------|-----------------|--------|
| 0 | Build a ±1 mg-resolution force measurement platform; characterise noise floor | ~$500 | In progress |
| 1 | Townsend Brown / Lifter force-vs-voltage curves in atmosphere and low vacuum | ~$300 | Not started |
| 2 | YBCO + RF field (Fetisov 2022 replication) | ~$800 | Not started |
| 3 | Integration experiments: cold-state Brown, Casimir geometry × Meissner, dielectric stack charge/discharge | TBD | Not started |

Expected timescale is **years**, not months. Any *"quick breakthrough"* timeline should be treated as a red flag.

## How to join us

We welcome:

- **Independent replications**, including failed ones — *especially* failed ones. That's what this field is actually short on.
- **Critical reviews** of any SOP, error analysis, or conclusion.
- **Literature additions and translations**, especially Russian and Japanese sources.
- **Hardware design improvements**, even if it's just *"your wiring diagram is wrong"*.

Open an Issue or PR; please follow the citation and error-bar conventions in the discipline rules above. We're not corporate — we'd rather chat than process tickets.

## Citation

```
Boundary Lab (Open Research Log).
https://github.com/singer0503/boundary-lab
Web: https://boundarylab.org (planned)
Maintainer: singer0503
```

Each release will be tagged with a Zenodo DOI (TBD).

## Maintainer's stance

We're open to any outcome, including *"every test showed zero effect."* If that turns out to be the final result, this repo's value lies in **documenting that conclusion in a public, reproducible way**.

Science doesn't progress from certainty. It progresses from honest uncertainty.
