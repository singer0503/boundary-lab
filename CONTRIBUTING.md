[English] | [繁體中文](CONTRIBUTING.zh-TW.md)

# Contributing to Boundary Lab

> Come play with us.

This isn't a corporate codebase. It's a hobbyist research log run by one
person and a long-term AI collaborator. We don't have a Jira board, a
sprint cycle, or a CLA. What we do have is a shared commitment to
rigorous, honest, openly-licensed science.

If that sounds good to you, here's how to join.

## Before you contribute

Please read these three documents first:

1. **[README.md](README.md)** — what we are and aren't.
2. **[The 8 discipline rules](README.md#scientific-discipline-the-8-non-negotiable-rules)** — non-negotiable.
3. **[SAFETY.md](SAFETY.md)** — if your contribution touches any hardware.

## What we welcome

In rough order of how much we want it:

1. **Independent replications** of our experiments — *especially failed ones*.
   This field is starved for replication. A null result you log into a
   public Issue is more valuable than ten breathless YouTube demos.
2. **Critical reviews** of our SOPs, error analyses, or conclusions. If you
   spot a flaw, say so. We'd rather have it pointed out by you here than by
   a reviewer at a journal.
3. **Better SOPs** — clearer wording, missed systematic errors, hardware
   alternatives that hit similar specs at lower cost.
4. **Literature additions** — papers we should know about, especially in
   Russian, Japanese, or Chinese. Translations of key passages are gold.
5. **Hardware design improvements** — wiring diagrams, BOM substitutions,
   PCB designs.
6. **Software** — analysis scripts, plotting utilities, automation glue.
7. **Translations** of docs into other languages. Currently we maintain
   English and 繁體中文; both must stay in sync.

## How to contribute

### Small things — open an Issue

If you found a typo, a broken link, a missed citation, or a confused
explanation, just open an Issue. No template required. We'll fix it.

### Replications and data — open a Discussion

If you replicated one of our experiments, the result (positive, negative,
or "I couldn't get it to run") goes in a GitHub Discussion under the
"Replications" category. Include:

- Which experiment / SOP version you ran.
- Your hardware (BOM substitutions if any).
- Your environment (location, temp, humidity, anything relevant).
- Raw data (link to your own repo or attach files).
- Your interpretation.

We will engage with replication reports seriously, regardless of result.

### Code, docs, hardware — open a PR

For larger contributions:

1. Fork the repo.
2. Create a branch named for what you're doing (`docs/improve-safety-section`,
   `analysis/add-allan-variance`, `hardware/cheaper-faraday-cage`).
3. Follow the discipline rules. Specifically:
   - Every claim cites.
   - Errors first (no number without an error bar).
   - No marketing language.
4. Open a PR. We'll review.

We don't promise fast turnaround. This is a side project for everyone
involved. But we promise honest review.

### Critical reviews — say it loudly

If you think we're wrong about something, say so. Open an Issue titled
"Critique: [thing]" and lay out your argument. We don't take this
personally. Most science gets done by people pointing out each other's
mistakes early enough to fix them.

## Style

- **Code**: Python 3.11+, formatted with `ruff`. Type hints encouraged.
- **Markdown**: GitHub-flavored. Tables for structured comparisons.
  Equations in LaTeX (`$inline$` or `$$display$$`).
- **Commits**: imperative mood, present tense, lowercase first word.
  `add Allan variance to noise-floor analysis`, not `Added it!!!`.
- **Tone in prose**: rigorous but warm. Allow contractions, the
  occasional self-deprecating aside. Tone in *rules* and *safety*
  sections stays terse and uncompromising.

## What we won't accept

- Contributions framed in marketing language ("breakthrough", "revolutionary").
- Patent claims of any kind. We don't patent. Period.
- Closed-source dependencies that block replication.
- Anything that bypasses the safety rules in SAFETY.md.
- Hostile or dismissive criticism. Sharp criticism is welcome; bad faith is not.

## Code of conduct (short version)

Be useful. Be honest. Be careful with people's time. Don't be a jerk.
That's it.

## Questions?

Open a Discussion. We'd rather chat than process tickets.

## Recognition

All contributors get listed in `CONTRIBUTORS.md` (TBD) and in the
acknowledgements of any paper that uses their work. If you'd rather stay
anonymous or use a handle, that's fine — just say so.

---

*Welcome aboard. Bring your error bars.*
