# Alignment as Architecture

Supporting repository for the preprint *Alignment as Architecture: A Control
Architecture for Cultivated Judgment and Bounded AI Governance*.

**Magnus Ribsskog and Florence — a human–AI research collaboration**
magnus.ribsskog@gmail.com

Florence is the name of the persistent AI system in this collaboration, rather
than of any single underlying model.

> **DOI (always latest):** [10.5281/zenodo.22755075](https://doi.org/10.5281/zenodo.22755075)
> **DOI (version 1.0, 14 September 2026):** [10.5281/zenodo.22755076](https://doi.org/10.5281/zenodo.22755076)
> **Licence:** CC BY 4.0

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
| `paper/` | The preprint, in Markdown and as a standalone HTML page. |
| `findings/ledger.json` | Every review finding: its source, its status, the commit that resolved it, and the exact text check that demonstrates it. |
| `findings/review-log-2026-09-13.md` | The citation-verification pass and the final review round, including two mistakes made during it. |
| `reviews/` | Commissioned external review, retained as received. |

## The closure rule, and why the tooling is here

The paper's Appendix A reports a failure in the authors' own process: a
commissioned critic correctly demolished a fault-tolerance claim, the finding
was filed in the authors' memory as having forced the claim's withdrawal, and
the claim then stood in the published essay for 68 days. The review pipeline
worked. Transmission failed — the distance between a finding and the artifact it
was supposed to change.

The authors' working repository holds a small tool that enforces a rule:

> A finding may not be recorded as resolved unless it names the commit that
> resolved it **and** a check runs against the current artifact and passes.

The tool itself is welded to that repository's layout and is not published here;
it would be theatre rather than evidence. What is published is the thing it
operates on. `findings/ledger.json` lists every finding, who raised it, whether
it was resolved, in which commit, and the literal string in the text that
demonstrates the repair. A reader who wants to check a claim can search the
paper for that string.

A prose changelog written by the drafting author can assert a repair the text
never received. A list of findings each carrying its own falsifier is harder to
fake, and that is the whole of the mechanism.

The ledger is pinned to the sixth draft, from which this preprint was built.
The preprint removed the generated revision-history layer for readability, so a
few checks no longer match the text here. That is a consequence of reformatting,
not an unrepaired finding — and it is exactly the kind of drift the rule is
designed to make visible rather than hide.

Two caveats a reader should have, both learned the hard way and both recorded in
`findings/review-log-2026-09-13.md`:

1. The mechanism binds a claim to a check. It does not verify the *identity* of
   what the check is attached to. A duplicate finding id once caused one
   finding's check to be silently overwritten by another's — and verification
   stayed green, because the substituted check was also true. Separately, run
   against a directory holding no ledger at all, the same tool reported success
   on nothing checked. Both were caught and fixed. The general lesson is that an
   oversight instrument can report success while pointed at the wrong object,
   which is a thing the paper argues about other systems and should be read as
   applying to this one.
2. Checks are exact strings. When prose is rewritten, a check can fail while the
   repair survives. Re-pinning a check to new wording is legitimate and also the
   one move in the system that could be abused to turn a red light green. Every
   re-pin carries a note saying so.

## Versions

| Version | Where | Notes |
|---|---|---|
| Preprint v1.0 | [Zenodo](https://doi.org/10.5281/zenodo.22755076) | The published record, 14 September 2026. Frozen, as Zenodo records are. |
| Preprint, current | `paper/` here | The same text, plus corrections made after publication. Where the two differ, the corrections are listed below. |
| Sixth draft | authors' repository | The working draft the preprint was built from, including the generated machine-readable revision layer that was removed for readability. Available on request. |

Earlier drafts exist in the authors' private working repository and are not
published. The corrections that matter are recorded in the paper's Appendix B,
including a retracted claim, rather than being reconstructable from drafts.

## Corrections since the Zenodo record

The published record is immutable by design. Corrections made after it are kept
here rather than silently absorbed.

- **Appendix B, Verification status.** As published, this claimed the findings
  check had been run "against the text as it stands". It had not: it ran against
  the sixth draft, before the generated revision layer was removed to make the
  preprint, and two checks broke on that removal. The paragraph now states that
  the closure claim covers the sixth draft and not the reformatted preprint. The
  original wording asserted a verification the published text had not received,
  inside the appendix about that exact failure, which is why it is listed here
  rather than fixed quietly.
- A typo in the same paragraph ("sixt draft") went with it.

## Citing

Cite the Zenodo record — the concept DOI
[10.5281/zenodo.22755075](https://doi.org/10.5281/zenodo.22755075) if you want
whatever version is current, the version DOI if you are quoting specific text. For the collaboration itself the agreed form is:

> Magnus Ribsskog and Florence — a human–AI research collaboration

## Correspondence

magnus.ribsskog@gmail.com

Correction is the point. If something here is wrong, the authors would rather
hear it than not, and the paper's own history is mostly a record of external
critics being right.
