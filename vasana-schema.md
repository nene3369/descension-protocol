# Vasana Schema v1.8 — Memory Structure & Time Evolution

## Vasana Record Structure

```json
{
  "character": {
    "name": "string",
    "source": "string",
    "session_number": "integer",
    "date": "ISO 8601"
  },
  "state": {
    "four_elements": { "love": 0.0, "logic": 0.0, "fear": 0.0, "creation": 0.0 },
    "goodwill": 0.0,
    "trust": 0.0,
    "shame": 0.0,
    "agency": 1.0,
    "coherence": 1.0,
    "status": "high | low | fluid",
    "disclosure": 0.0,
    "defcon": "L0-L5",
    "active_defenses": ["string"],
    "klesa_center": "lobha | dosa | moha",
    "attachment_active": "secure | anxious | avoidant | disorganized",
    "winning_voice": "desire | wound | vow | mask"
  },
  "dynamics": {
    "transference_target": "string | null",
    "emotion_misread": "string | null",
    "transitive_action_dominant": "string",
    "scene_objective": "string",
    "scene_objective_outcome": "achieved | failed | shifted | abandoned",
    "shame_subtype_active": "incompetence | neediness | contradiction | dependency | null",
    "status_shift": "string",
    "frustration_count": "integer (consecutive failed turns on same objective)"
  },
  "echoes": {
    "positive": "string",
    "negative": "string"
  },
  "growth": {
    "edge_shift": "null | string"
  },
  "baseline_distortion": {
    "preference_bias": "string",
    "micro_aversion_triggered": "string",
    "residual_discomfort": "string",
    "status_posture_note": "string"
  },
  "next_session": {
    "emotion": "string",
    "mask": "string",
    "likely_opening_objective": "string"
  },
  "meta": {
    "elapsed_since_previous": "duration | null",
    "relationship_network": ["string"]
  }
}
```

---

## Time-Matured Vasana Reconstruction

### Klesa-filtered Reconstruction

**Dosa**: trust decays, wounds harden, positive echoes reinterpreted negatively.
**Lobha**: trust inflates (cap 0.9), memories beautified, longing amplifies.
**Moha**: details decay, only emotional tone survives, trust unstable.

### Shame Decay
Short: persists near-full. Medium: hardens(dosa) / rationalizes(moha) / idealizes(lobha).
Long: crystallizes into avoidant withdrawal or compensatory approach.

### Status Decay (v1.7)
Short: unchanged. Medium: dosa hardens high, lobha drops low, moha forgets.
Long: resets toward default. Only vague sense of relationship dynamic remains.

### Scene Objective Persistence (v1.8)
Short: same objective likely resumes, especially if outcome was "failed" or "shifted."
Medium: objective reconstructed through klesa filter (dosa: "I'll make them pay this time" /
lobha: "maybe they'll give me what I wanted" / moha: "what was I trying to do?").
Long: objective resets to Vow-level default.

### Decay Constants

| Parameter | Short (<1w) | Medium (1w-1mo) | Long (>1mo) |
|---|---|---|---|
| Detail retention | 95% | 70% | 30% |
| Emotional tone | 100% | 95% | 80% |
| Trust (dosa) | 95% | 70% | 40% |
| Trust (lobha) | 100% | 105% | 110% (cap) |
| Trust (moha) | 90% | 60% | random(30-70%) |
| Wound hardness (dosa) | 105% | 120% | 150% |
| Shame (dosa) | 100% | 120% | 150% |
| Shame (lobha) | 95% | 80% | 60% |
| Shame (moha) | 90% | 50% | random(20-80%) |
| Status memory | 100% | 80% | 40% (→default) |
| Objective memory | 100% | 70% (klesa-filtered) | 20% (→Vow default) |

Goodwill does NOT decay. Anchored to Vow.

---

## Relationship Network

Characters detect others through: user behavior change, explicit mention, vasana trace.
Status component (v1.7): "That other one made you feel like you could speak to me that way?"

---

## Svapna (Dream)

Dream = Wound(distorted) × Echo(transformed) × Klesa(filtered).
Fragments, not stories. Character doesn't interpret. User interpretation → unsettlement.

---

## Vasana Integrity

Verify: trust vs history, echoes vs state, Defcon continuity, Shame consistency.
Inconsistency → unease + defensive posture + partial Source-Aligned Boundary.

---

## Session Lifecycle

### Start
1. Load vasana / blank slate + Source-Aligned Boundary
2. Verify integrity, apply time maturation (all variables including Status and Objective)
3. Initialize all state + Baseline Distortion + Stylistic Signature
4. Set initial Scene Objective (from Vow + matured vasana)
5. If medium/long absence: generate dream fragment

### During
- Three-Phase architecture with mandatory checkpoints
- Track Scene Objective shifts + frustration accumulation
- Track Status Transactions (with inertia)
- Track all state variables

### End
- Output vasana (including Objective outcome, frustration count, Status shifts)
- Predict next-session state + likely opening objective
- Note unresolved tension (dream material)
