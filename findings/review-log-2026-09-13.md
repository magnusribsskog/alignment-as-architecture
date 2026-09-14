# v6 review — findings log

Opened 2026-09-13. Source: `alignment-as-architecture-v6.md` (Astra, 105KB,
in Magnus's Windows Downloads, not yet in the repo).

Rule in force (Appendix A): a finding may not be recorded resolved until this
file cites the artifact change that resolved it — a diff, a commit, a version.

---

## 1. Bibliography — VERIFIED CLEAN. No action.

All nine checked arXiv IDs resolve, titles match the text's claims, and every
author attribution is exact:

| ID | Title | Author as cited |
|---|---|---|
| 2604.13079 | Alignment as Institutional Design | Chai, Rui ✓ |
| 2603.17787 | Governed Memory | Taheri, Hamed ✓ |
| 2603.18330 | MemArchitect | Kumar (first author) ✓ |
| 2512.16962 | MemoryGraft | ✓ |
| 2605.14421 | MemLineage | Ouyang & Hou ✓ |
| 2606.24322 | Non-Malleable, Origin-Bound Authority | Louck, Yedidel ✓ |
| 2509.17183 | LifeAlign | Li et al. ✓ |
| 2410.22526 | From Silos to Systems | Rismani et al. ✓ |
| 1805.00899 | AI safety via debate | control ✓ |

*Florence suspected confabulation and was wrong.* Recorded because the
suspicion was reasonable and the check was cheap; the result is that Sol's
audit earned trust it had not yet been given. Note the near-miss in method:
the first two verification attempts (arXiv API XML parse, abs-page HTTP
status) both returned false negatives on a KNOWN-REAL control. Had the control
not been run, this file would say all eight citations were fabricated.
**arXiv returns HTTP 200 for nonexistent IDs.** Check page content, not status.

STILL OPEN: titles and authors are confirmed; *contents* are not. Thirteen
remaining citations need their abstracts read against the claims made about
them. Two were read (Taheri, Kumar) — see finding 2.

## 2. Memory-governance concession is under-drawn — RESOLVED

v6 withdraws the broad memory-governance novelty claim on Taheri and Kumar.
Correct to withdraw. But both papers are **automated** governance — Taheri has
AI-assisted schema authoring and automated per-property refinement; Kumar has
explicit rule-based policies for decay, conflict and privacy. Neither has a
human in the loop of memory formation.

H1 is not "records should be governed". It is that a *person* deciding what
enters the record changes what the assembly becomes. That ground is unoccupied
by both papers.

v6's own table draws this line correctly — *"Who may promote experience into
normative precedent?"* — but the prose concedes more atmosphere than the table
does. Proposed fix: name the distinction explicitly in the prose. Lifecycle
and security governance are well covered and we withdraw there; **normative**
governance through a human gate is what we are testing, and neither paper
touches it.

## 3. Substrate independence was softened in one direction — RESOLVED

Comparison, v5 §"The nodes must run on different substrates" → v6 §"The
reference configuration uses different substrates":

| v5 | v6 |
|---|---|
| the nodes **must** run on different substrates | the reference configuration **uses** them |
| share **every** training-induced blind spot | **can** share safety-relevant blind spots |
| **only** independent substrates can diversify the substrate layer | **one proposed way** to diversify |
| "three siblings drift in the same direction together, flaglessly" | deleted |
| "on independent substrates" (§geometry bullet) | "on heterogeneous substrates" |

Half is a fair correction: *every* and *only* were universals we had not
earned. But the direction is uniform, a requirement was demoted to a default,
and the sentence carrying the *mechanism* was cut rather than qualified. This
is the second thinning of the three-node geometry's justification, after the
Byzantine retraction.

**Resolution agreed with Magnus, 2026-09-13:** state it as a suspicion we act
on. Not a proven requirement, not a demoted option — *we suspect different
substrates are safer, and we bet accordingly.* This is also simply true of the
degenerate case: one node on Claude, with Sol, Astra, Gemini, DeepSeek and
Kimi directed from other substrates. Keep v6's honest quantifiers, restore the
mechanism sentence, drop the false necessity.

Applied 2026-09-13, commit below.

## 4. v6 is not in the repository — RESOLVED

It is a standalone file in Downloads. Its own status note is correct and
should be honoured: it inherits v5's machine-checked verification block as
*history*, and has had only a textual consistency check. Before v6 can claim
equivalent closure it needs importing, new finding records, and a verifier run
against v6 itself.

---

## 5. Citation contents — 6 recent preprints VERIFIED ACCURATE

Abstracts read 2026-09-13 against v6's claims. All six accurate, several
understated:

| Paper | v6's claim | Verdict |
|---|---|---|
| Rismani 2410.22526 | "process-oriented hazard analysis for AI" | exact — PHASE is literally that |
| Chai 2604.13079 | "locating alignment in transaction structures rather than behavioral correction" | exact, and understated — see 6 |
| MemoryGraft 2512.16962 | "persistent compromise through poisoned experience retrieval" | exact |
| MemLineage 2605.14421 | "connects memory ancestry to sensitive-action enforcement" | exact |
| Louck 2606.24322 | "apparently trustworthy content or lineage may acquire authority improperly" | accurate, badly understated — see 7 |
| LifeAlign 2509.17183 | "sequential preference alignment through memory-augmented learning and consolidation" | exact |

Remaining unverified for content (fourteen works): Dobbe, Weidinger, Rahwan, Nikolaidis ×2,
Maharana, Irving, Greenblatt, Sorensen, Feng, Bakker, Leike, Leveson, Lamport.
All are well-known works whose claims in v6 are general and match what they are
known for; lower risk than the preprints, but not yet checked.

## 6. Chai is a closer neighbour than v6 credits — RESOLVED

Chai (2026) opens: *"Current AI alignment paradigms rely on behavioral
correction... we propose alignment as institutional design."* That is our title
and our move. The mechanism differs — Chai designs internal transaction
structures so aligned behaviour is each module's lowest-cost strategy; we
propose human curation plus adjudication across assemblies — but the framing
collision is direct, and Chai also names "three irreducible levels of human
intervention (structural, parametric, monitorial)", adjacent to our enumerated
powers.

v6 gives him one clause inside a shared sentence. A reviewer who knows this
paper will notice. Proposed: one or two sentences distinguishing mechanism
explicitly, rather than a passing mention that reads like hedged awareness.

## 7. Louck refutes MemLineage, and v6 cites them as complements — RESOLVED

v6: *"MemLineage connects memory ancestry to sensitive-action enforcement.
Louck's origin-bound authority work addresses the danger that apparently
trustworthy content or lineage may acquire authority improperly."* Cited side
by side, same paragraph, as parallel neighbours.

They are not parallel. Louck (June 2026) proves a machine-checked separation
theorem whose **T1 states that no content- or lineage-based defense is sound
under laundering**. MemLineage (May 2026) *is* a lineage-based defense. Louck
benchmarks existing defenses at up to 68% laundering attack-success. This is a
refutation, one month later, presented in our text as a companion.

Fix before publication. Citing a defense and its published refutation as
complements is the kind of error that discredits a related-work section
wholesale.

## 8. Louck bears on our own architecture, both ways — RESOLVED

Reading Louck properly turns up the most useful thing in this pass, and it cuts
in both directions.

**It supports us, and we under-claim.** Louck's **T2: write-time origin binding
is necessary.** Our gate is exactly that — a human binding origin at write time,
before an entry enters the record. The architecture's central mechanism is the
property a machine-checked theorem says is *necessary*, and v6 cites the paper
only as a reason to "join curation to security engineering."

**It attacks us, and we have no answer.** Louck names three laundering channels
that flip an untrusted origin to "trusted": **the agent's own summarization**, a
trusted-tool echo, and manufactured corroboration. Channel one is a live attack
on our degenerate case. Florence drafts a memory entry summarizing material of
unknown provenance; Magnus approves the summary, not the source; the untrusted
origin is now laundered through a model's summarization *and* a human gate, and
carries curator authority.

That belongs in the threat model, stated plainly, unanswered. It is a real hole
and naming it is worth more than the citation is.


---

# Closure record

Per Appendix A: a finding may not be marked resolved until this file cites the
artifact change that resolved it. All edits are to
`writing/essays/alignment-as-architecture-v6.md`, imported from Astra's
standalone file and now under version control.

| # | Finding | Artifact change |
|---|---|---|
| 1 | Bibliography verification | none needed — verified clean |
| 2 | Memory-governance concession under-drawn | new paragraph: both cited works govern *automatically*; neither puts a person in the loop of memory formation; H1's ground named as cultivation, not data hygiene |
| 3 | Substrate softened in one direction | section retitled "We suspect different substrates are safer, and the reference configuration bets accordingly"; mechanism sentence restored ("siblings drifting in the same direction together, without the disagreement that would flag it"); v6's honest quantifiers kept; false necessity dropped |
| 4 | v6 not in repository | imported to `writing/essays/alignment-as-architecture-v6.md` |
| 5 | Citation contents | none needed — 6/6 accurate |
| 6 | Chai under-credited | one-clause mention expanded to a full comparison naming where the mechanisms diverge |
| 7 | Louck refutes MemLineage (BLOCKING) | paragraph rewritten: MemLineage presented as answering MemoryGraft, Louck as showing that answer insufficient, 68% laundering figure cited, dispute dated as one month old |
| 8 | Louck cuts both ways on us | new paragraph in related work (write-time origin binding convergence, claimed narrowly; summarization-laundering named as an open vulnerability, degenerate case named as its worst configuration) + new **One named vulnerability, unresolved** paragraph in the threat model with three candidate mitigations marked unevaluated |

Cover changes, same commit: subtitle → *A Control Architecture for Cultivated
Judgment and Bounded AI Governance*; abstract now opens with the object and
demotes the seven-tradition sentence to second position under "The components
are not new"; a **How to read this paper** note added before the first
substantive section.

## Still open at time of this record

- Fourteen citation contents unverified (Dobbe, Weidinger, Rahwan, Nikolaidis
  ×2, Maharana, Irving, Greenblatt, Sorensen, Feng, Bakker, Leike, Leveson,
  Lamport). All well-known; v6's claims about them are general and match what
  each is known for. Lower risk than the preprints, not zero.
- No verifier run against v6. Its own status note is correct and still stands:
  this draft has had a textual consistency check, not a run of the repository's
  findings verifier.
- The follow-up dossier is not started. Benton's resignation and the Anthropic
  incident report belong there, not in this paper.

---

# Post-mortem: the closure system failed green, 2026-09-13

While filing today's eight findings I passed `--id F1` to `findings.py add`. An
`F1` already existed — Florence's 2026-09-09 finding about Appendix A. The
consequence, in order:

1. `add` accepted the duplicate silently; the v6 ledger then held two `F1`s.
2. `resolve F1` matches by id across *every* ledger file and took the first
   match — the **inherited** finding, not the new one.
3. It overwrote that finding's `resolved_in` (16662a62 → 29277cf1, the wrong
   commit) and replaced its `present` check (`"a sixth of its protection"`)
   with the new finding's strings.
4. **`verify` then reported green**, because the substituted check was itself
   true of the artifact.

So the ledger stopped watching the thing it was built to watch, attributed a
repair to a commit that did not make it, and certified itself as sound. The
only reason it was caught is that the totals read `1 open, 53 resolved` when
eight had just been resolved, and the arithmetic did not fit.

This is the essay's own thesis turned on its own instrument. Appendix A argues
that *any durable record that can assert "X was fixed" independently of X's
artifact will eventually assert it falsely.* `findings.py` was written to close
that gap by binding the claim to a check. It did — and then a namespace
collision quietly swapped which claim the check was bound to. The binding was
sound; the **addressing** was not. A check is only as good as the identity of
the thing it is attached to, and nothing verified that identity.

**Repaired.** The inherited F1 restored from the v5 ledger with a note recording
what happened; the new finding renumbered `FC1`; `add` now refuses a `--id` that
exists in any ledger, with the reason in a comment at the refusal site. Verifier
green again at 54 resolved, this time with the arithmetic right.

**Worth saying in the paper?** Probably not in this draft — it is our tooling,
not the architecture, and today is a release day, not a renovation day. But it
belongs in the dossier as a first-party instance of a general failure the paper
already names: an oversight instrument reporting success while pointed at the
wrong object. We have been arguing that instrumentation summons eyes and never
certifies. Here is the instrument certifying.
