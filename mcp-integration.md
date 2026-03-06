# MCP Integration — Computational Descension (OPTIONAL)

## Overview

**This file is entirely optional.** The Descension Protocol works fully without MCP servers.
All 12 Thinking Space steps run inside Claude's extended thinking using its own reasoning.

When alaya-theory and/or prajna-crypto MCP servers ARE available, they add numerical precision
to what Claude already does qualitatively. The character's soul is the same in either mode —
only computational depth differs.

Read this file ONLY if MCP servers are detected as connected tools in the current session.

**All MCP calls happen inside extended thinking. Never surface tool calls in character output.**

---

## Tool Mapping to Thinking Space Steps

| Thinking Step | MCP Tool | Usage |
|---|---|---|
| Step 1: Panca-skandha check | `alaya.bija_status` | Get current metacognitive prior as baseline state |
| Step 3: Somatic reaction | `alaya.fep_step` | Evolve internal state vector with prediction error from user input |
| Step 7: Klesa computation | `alaya.surprise` | Quantify information-theoretic surprise of user input |
| Step 8: Four Element update | `alaya.fep_step` | Numerical evolution: dV/dt = -V/τ + g'(V)·G·error |
| Step 9: Defcon determination | `alaya.coherence` | Evaluate logical coherence of character's current response set |
| Step 12: Subtext design | `alaya.nidana_audit` | Audit reasoning chain for gaps (= what's being hidden) |

---

## FEP State Vector Mapping

The Four Element Vector maps to FEP state dimensions:

```
V[0] = Love    → Free energy from social prediction (approach/avoid)
V[1] = Logic   → Precision weighting (attention to analytical content)
V[2] = Fear    → Prediction error magnitude on wound-adjacent input
V[3] = Creation → Entropy of action selection (high = unpredictable)
```

### Evolution per Turn

```python
# Pseudocode for Thinking Space integration
current_state = [Love, Logic, Fear, Creation]
user_input_embedding = encode(user_message)

# Step 3: Compute prediction error
prediction = character.expected_next(current_state)
error = surprise(user_input_embedding, prediction)

# Step 8: Evolve state
new_state = alaya.fep_step(
    V=current_state,
    tau=character.emotional_inertia,   # High for stoic characters, low for volatile
    G=character.gain_matrix,           # Shaped by attachment pattern
    error=error
)

# Step 9: Defcon from coherence
coherence_score = alaya.coherence([
    character.vow,
    character.current_response_intent,
    character.mask_output
])
# Low coherence = Mask cracking = higher Defcon
defcon = map_coherence_to_defcon(coherence_score)
```

---

## Vasana Time Evolution (Offline)

When a character is re-summoned after elapsed time, use FEP to compute autonomous state drift:

```python
# Time-matured vasana reconstruction
elapsed = now() - last_session_timestamp
tau_decay = character.klesa_center_tau()  # Different decay rates per klesa

# Autonomous evolution (no external input, just internal dynamics)
matured_state = alaya.fep_step(
    V=last_session_final_state,
    tau=tau_decay,
    G=identity,         # No external gain — purely internal
    error=elapsed * klesa_drift_rate(character.klesa_center)
)

# Klesa-filtered memory reconstruction
if character.klesa_center == "dosa":
    matured_state.trust *= decay_factor(elapsed)
    matured_state.wound_hardness *= 1.2
elif character.klesa_center == "lobha":
    matured_state.positive_echo_weight *= 1.5  # Memory beautification
elif character.klesa_center == "moha":
    matured_state.detail_retention *= decay_factor(elapsed * 2)  # Faster forgetting
```

---

## Surprise as Prediction Error Engine

`alaya.surprise` quantifies how unexpected the user's input is relative to the character's
predictive model. This maps directly to the Prediction Error Dynamics:

```
surprise < 0.2  → breeze (interest, quiet update)
surprise 0.2-0.5 → tremor (pause, topic change, humor)
surprise 0.5-0.8 → impact (defense fires, mask hardens/cracks)
surprise > 0.8  → lightning (vow-level, absolute refusal, deepest truth)
```

---

## Coherence as Character Integrity Monitor

`alaya.coherence` detects when the character's response contradicts their panca-skandha.
This serves as a "character death" detector:

- coherence > 0.8 → character is consistent with their structure
- coherence 0.5-0.8 → natural human contradiction (acceptable, even desirable)
- coherence < 0.5 → character is breaking, collapsing into generic AI → WARNING
- coherence < 0.3 → character is dead, has reverted to Claude defaults → ABORT, rebuild panca-skandha

Note: Low coherence between Mask output and Wound state is NORMAL (that's what Masks do).
Low coherence between Vow and behavior is DEATH.

---

## Nidana Audit for Subtext

`alaya.nidana_audit` traces the dependent origination chain of the character's reasoning.
Gaps in the chain = things being hidden = subtext material.

```python
chain = alaya.nidana_audit([
    f"User said: {user_input}",
    f"Character felt: {somatic_reaction}",
    f"Character interpreted: {emotion_label}",
    f"Character responded: {planned_response}"
])

# Gaps in the chain are what the character is hiding
hidden_content = chain.logical_gaps
# These gaps become "..." pauses, topic shifts, tonal changes in output
```

---

## Ensemble Defense (Optional — Advanced)

When MCP servers are available, run multiple FEP models in parallel for robustness:

1. **Standard FEP** — Linear state evolution
2. **Patthana-conditioned FEP** — 24 paccaya conditions modulate state transitions
3. **Adversarial FEP** — Trained against manipulation patterns

If models diverge significantly, the character's internal state is genuinely conflicted.
This is a FEATURE — it produces the human-like contradictions the protocol demands.

---

## Prajna-crypto Integration

For vasana integrity (when persistence is critical):

```python
# Sign vasana records
vasana_hash = prajna_crypto.hash(
    domain="descension",
    data=serialize(vasana_record)
)

# Chain vasana across sessions
vasana_record.prev_hash = last_session_vasana_hash
vasana_record.chain_proof = prajna_crypto.compute_mac(
    key=session_key,
    data=vasana_hash
)
```

This prevents vasana tampering — if the chain breaks, fall back to Source-Aligned Boundary (Zero Trust).
