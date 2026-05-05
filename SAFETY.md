[English] | [繁體中文](SAFETY.zh-TW.md)

# Safety Procedures — Boundary Lab

> Some experiments here can kill you. Read this before touching anything.

This document is binding. If you are replicating any experiment from this
repository, you must read and understand the relevant section before starting.
The maintainer accepts no liability for harm; you accept full responsibility
for your own safety.

---

## 0. The five non-negotiable habits

Adopt these regardless of which experiment you're running:

1. **Never work alone on hazardous experiments.** A second competent person
   in the room or audible to a panic button.
2. **One hand rule for anything > 50 V DC or > 25 V AC.** Keep your other
   hand in a pocket. This is what stops current crossing your chest.
3. **Discharge before you handle.** Every capacitor, every electrode, every
   inductor — short to ground via a discharge stick with a 1 MΩ ballast
   resistor before touching.
4. **Eye protection on whenever the experiment is energised.** ANSI Z87.1
   minimum.
5. **Phone within arm's reach, set to dial emergency services with one tap.**
   Pre-dial the local number for your country.

If you can't honour one of these for a given session, do not run the experiment
that session.

---

## 1. High voltage (>1 kV)

Relevant phases: 1, 3.

### Hazards
- Cardiac arrest from current crossing chest (~50 mA AC, less for DC into vulnerable timing).
- Burns from arc flash.
- Eye damage from UV in arc.
- Equipment damage from unexpected discharge.

### Required equipment
- **Class 0 insulating gloves** (rated 1000 V working, tested annually).
- **Insulating mat** under your feet during operation.
- **Discharge stick** with 1 MΩ ballast resistor.
- **E-stop button** wired in series with the HV supply, within arm's reach.
- **Grounded HV-rated probes** for measurement.
- **Safety glasses with UV protection.**

### Procedure (Phase 1 lifter / asymmetric capacitor)
1. Wire all connections with the supply unplugged from mains.
2. Verify e-stop kills the supply (test before HV is engaged).
3. Walk back from the test article. Two-metre minimum.
4. Bring up voltage slowly via variac. Watch the ammeter.
5. To touch any electrode: power off → wait 30 s → discharge stick to each
   capacitor terminal → confirm ground potential with HV probe → only then
   approach.

### Forbidden
- Working on HV alone.
- Touching anything energised.
- Bypassing interlocks "just to test something quickly."
- Using non-rated wire (use HV silicone, ≥ 40 kV/mm).
- Routing HV near body parts or mains AC wiring.

---

## 2. Cryogenics (Liquid Nitrogen, LN₂)

Relevant phases: 2, 3.

### Hazards
- **Asphyxiation** — 1 L of LN₂ → ~700 L of N₂ gas. In a small enclosed
  space, you can suffocate before noticing.
- **Cryogenic burns** — instant tissue damage from contact or splash.
- **Eye damage** from splash.
- **Pressure rupture** from sealed containers (LN₂ in a sealed flask is a
  bomb).

### Required equipment
- **Open or actively-ventilated workspace.** Outdoors or fume hood. Never a
  closed room.
- **Cryo gloves** (loose-fitting; you must be able to throw them off if LN₂
  gets inside).
- **Safety goggles**, full-seal type, not just glasses.
- **Long sleeves and trousers**, closed-toe shoes.
- **Open-vented dewar** for storage. Never a sealed container.
- **Oxygen monitor** if working in any partially-enclosed space (small lab,
  garage). Alarms below 19.5%.

### Procedure
1. Pour slowly. Splash is the main injury source.
2. Use a tundish or funnel; don't pour from one open container directly.
3. Never put your hand or face above the dewar opening when pouring or
   when LN₂ is being added.
4. After a session, leave the workspace ventilated for 30 min before
   re-entering with no monitor.

### Forbidden
- Sealed containers of LN₂.
- LN₂ in an enclosed unventilated room.
- Pouring with bare hands.
- Tasting, splashing, or any "look how cool this is" demonstrations.

---

## 3. Strong magnets (N42 and stronger)

Relevant phases: 2, 3.

### Hazards
- **Pinch injuries** — N52 magnets can clamp through a finger.
- **Projectiles** — magnets fly together at high speed; chips of magnet can
  spall off in collision.
- **Pacemaker / ICD interference** at field strengths over a few mT.
- **Erasure** of magnetic media, credit cards, mechanical watches.
- **Steel objects** (tools, jewellery) become projectiles in the field.

### Required equipment
- **Cut-resistant gloves.**
- **Safety glasses.**
- **Non-ferrous tools** (brass, plastic, aluminium).
- **Marked "magnet zone"** on the floor — no steel, no electronics, no
  pacemakers within 1 m.

### Procedure
- Always handle one at a time.
- Separate magnets with non-ferrous spacers when storing.
- Approach a fixed magnet from the side, not the face.

### Forbidden
- Anyone with a pacemaker, ICD, or cochlear implant within 1 m of a strong
  magnet, period.
- Carrying loose magnets in pockets.
- Removing magnets stuck to ferrous surfaces by direct pull (use a sliding
  shim).

---

## 4. Vacuum chambers

Relevant phase: 1 (low vacuum lifter test), eventually 3.

### Hazards
- **Implosion** — atmospheric pressure on a chamber wall is ~10 tonnes per
  square metre. Glass household containers fail violently.
- **Flying glass / shrapnel.**

### Required equipment
- **Rated vacuum vessel** — purpose-built steel or thick acrylic with
  pressure rating documented. Not Mason jars. Not Pyrex.
- **Pressure relief valve** sized for your pump.
- **Polycarbonate shield** between you and the chamber during pump-down.

### Procedure
- Pump down behind a shield.
- Visually inspect chamber and seals before each session.
- Vent slowly — sudden inrush can damage internal samples and (if there's
  any LN₂ inside) re-condense oxygen, which is an explosion hazard.

### Forbidden
- Household glass under vacuum.
- Cracked or scratched acrylic chambers.
- Working with LN₂ inside a chamber unless you fully understand
  liquid-oxygen condensation hazards.

---

## 5. Electrolytic and high-voltage capacitors

Relevant phases: 1, 3.

### Hazards
- High-voltage caps store lethal charge for hours after disconnection.
- Reverse-polarity electrolytic caps can rupture / vent / explode.

### Procedure
- Always discharge with a stick (1 MΩ ballast) for ≥ 5× the RC time
  constant before any contact.
- Verify with a meter on the highest range.
- Only then touch.

### Forbidden
- "It's been off for an hour, should be fine."
- Shorting capacitors directly to ground without a ballast resistor —
  that's an arc flash waiting to happen.

---

## 6. Materials

### YBCO (Yttrium Barium Copper Oxide)
- Buy commercial pellets / powder. **Do not synthesise yourself.**
- Barium compounds are toxic — no eating, drinking, smoking near them.
- Wash hands after handling.
- Disposal: treat as heavy-metal hazardous waste.

### RF generators
- Even at low power, prolonged exposure to 50 MHz fields near the body is
  not well characterised. Distance + time = your friends.

---

## 7. Pre-experiment safety checklist

Before powering on any experiment, mentally walk through:

- [ ] Have I read the relevant section above today?
- [ ] Is a second competent person available?
- [ ] Is the e-stop tested and within arm's reach?
- [ ] Is my phone unlocked and within reach with emergency dial ready?
- [ ] Are bystanders at safe distance?
- [ ] Do I have a clear "abort path" — what do I do if X goes wrong?
- [ ] Is the workspace ventilated (if cryo / fumes)?

If any answer is "no" or "I'm not sure" — pause. Reset. Don't push through.

---

## 8. When to stop

Stop the experiment immediately if:

- Anything smells of ozone, burning insulation, or hot metal.
- You hear arcing or buzzing from somewhere unexpected.
- You feel a tingle from any surface you're touching.
- A meter reads outside expected range and you can't explain why.
- Ventilation fails during cryo work.
- Any bystander reports feeling unwell.

Stopping costs almost nothing. Restarting after a fire, a shock, or an
asphyxiation costs everything.

---

## 9. Reporting incidents

If something dangerous happens — even if no one was hurt — file a report
in `reports/safety-incidents/<date>-<short-description>.md` with:

- What happened.
- What was supposed to happen.
- Root cause.
- What changes to SOP / equipment / procedure prevent recurrence.

This is not a blame log. It is a learning artefact. Future contributors
need to see how the lab actually behaved, not how we wished it had.

---

*Last review: 2026-05-05. SOP changes that affect safety must update this
file and bump its version in git.*
