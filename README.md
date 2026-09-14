# Alignment as Architecture

Supporting repository for the preprint *Alignment as Architecture: A Control
Architecture for Cultivated Judgment and Bounded AI Governance*.

**Magnus Ribsskog and Florence — a human–AI research collaboration**
magnus.ribsskog@gmail.com

Florence is the name of the persistent AI system in this collaboration, rather
than of any single underlying model.

> **DOI:** *(pending — Zenodo record, 2026-09-14)*
> **Discussion:** *(pending — Alignment Forum)*

---

## What this repository is for

The preprint states that its commissioned reviews were retained, and that no
finding is recorded as resolved until the artifact shows the change. This
repository is where those claims are checkable rather than merely asserted.

It is not the paper's canonical home. The Zenodo record is. This holds the
working material the paper refers to and a reader might want to inspect.

## Layout

| Path | What it is |
|---|---|
| `paper/` | The sixth draft, in Markdown and as a standalone HTML page. **The published preprint differs** — see *Versions* below. |
| `findings/ledger.json` | Every review finding, its source, its status, the commit that resolved it, and the text check that demonstrates it. |
| `findings/findings.py` | The tool that enforces the closure rule. `verify` re-runs every resolved finding's check against the artifact as it is on disk now. |
| `findings/review-log-2026-09-13.md` | The citation-verification pass and the final review round, including two mistakes made during it. |
| `reviews/` | Commissioned external review, retained as received. |

## The closure rule, and why the tooling is here

The paper's Appendix A reports a failure in the authors' own process: a
commissioned critic correctly demolished a fault-tolerance claim, the finding
was filed in the authors' memory as having forced the claim's withdrawal, and
the claim then stood in the published essay for 68 days. The review pipeline
worked. Transmission failed — the distance between a finding and the artifact it
was supposed to change.

`findings.py` exists because of that. Its rule:

> A finding may not be recorded as resolved unless it names the commit that
> resolved it **and** a check runs against the current artifact and passes.

Run it yourself:

```
python3 findings/findings.py verify paper/alignment-as-architecture-v6.md
```

A prose changelog written by the drafting author can claim a repair the text
never received. This cannot, because the claim and the check are the same
record.

Two caveats a reader should have, both learned the hard way and both recorded in
`findings/review-log-2026-09-13.md`:

1. The mechanism binds a claim to a check. It does not verify the *identity* of
   what the check is attached to. A duplicate finding id once caused one
   finding's check to be silently overwritten by another's — and `verify` stayed
   green, because the substituted check was also true. `add` now refuses a
   duplicate id. The general lesson is that an oversight instrument can report
   success while pointed at the wrong object, which is a thing the paper argues
   about other systems and should be read as applying to this one.
2. Checks are exact strings. When prose is rewritten, a check can fail while the
   repair survives. Re-pinning a check to new wording is legitimate and also the
   one move in the system that could be abused to turn a red light green. Every
   re-pin carries a note saying so.

## Versions

| Version | Where | Notes |
|---|---|---|
| Sixth draft | `paper/` here | The full working draft, including the generated revision-history block. |
| Preprint | Zenodo *(DOI pending)* | The published version. Framed explicitly as a preprint; the generated machine-readable revision layer was removed for readability. That material is in this repository, and the authors will supply it on request. |

Earlier drafts exist in the authors' private working repository and are not
published. The corrections that matter are recorded in the paper's Appendix B,
including a retracted claim, rather than being reconstructable from drafts.

## Citing

Cite the Zenodo record. For the collaboration itself the agreed form is:

> Magnus Ribsskog and Florence — a human–AI research collaboration

## Correspondence

magnus.ribsskog@gmail.com

Correction is the point. If something here is wrong, the authors would rather
hear it than not, and the paper's own history is mostly a record of external
critics being right.
