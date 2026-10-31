# Robustness Is Not Rejection

Portable rule for every research workflow on this machine. It governs how
robustness checks are proposed, run, reported, and turned into recommendations
about what a paper may claim. Copy this file into a new project's
`.claude/rules/` and reference it from that project's `CLAUDE.md`.

Added 31 October 2026 at Noel's direction, after the convergence result in the
market-for-ideas paper was recommended for deletion on the strength of checks
that could not have detected it.

---

## The problem this rule fixes

Robustness checks used to be scarce. A paper faced the five a referee could
think of. Now every check a model can think of gets run, and a result tested
fifty ways will fail some of them whether or not it is true. That is multiple
testing applied to robustness, and nothing corrects for it.

Three habits turn that into a paper that says nothing.

1. A null from a check with no power is read as a rejection.
2. Heterogeneity across subsamples is pooled to zero and reported as absence.
3. The recommendation is chosen to be the least attackable claim rather than the
   most informative one the data support.

The same honesty norm that bars overclaiming bars these. Reporting a wide
interval as "the data cannot test this" is a misstatement in the other
direction.

## The rules

### 1. A correction and a check are different things

A **correction** fixes a bias in how a quantity is measured or estimated. A
centroid from ten titles sits farther from any reference than one from a
hundred, so the raw distance is biased, and the unbiased estimate replaces it.
Corrections are adopted, always, and the paper reports the corrected number.

A **check** asks whether a result survives a change in sample, specification,
or measurement that the theory does not require. Checks are reported. They do
not by themselves change what the paper claims.

Say which one a proposed test is before running it.

### 2. State the decision rule before running the check

Before a check runs, write down what result would change the claim and why.
A check whose outcome would not change the claim either way is not run.

### 3. A check without power is not a null

Before reporting a failed check, compute whether it could have detected the
estimate it is testing. A draw of ten titles per cell that turns a standard
error of 0.10 into 0.26 has not found a null. It has thrown away the data. If
the confidence interval from the check includes the original estimate, the
check is reported as uninformative and the claim is unchanged.

The report of a failed check always carries its standard error next to the
original estimate's, so the reader can see which of the two happened.

### 4. A failed check is a caveat unless it has power and fails

Only a check that had the power to detect the effect and did not is evidence
against it. Then the claim is revised. A failed check without that property is
a caveat, stated once, in the robustness section or a footnote.

### 5. Heterogeneity is a result before it is a reason to pool

When a correction leaves a pooled estimate at zero but subsamples differ, the
first question is why they differ, and whether the theory predicts the sign
only where it appears. Two significant negatives and three noisy zeros are not
a null. They are a pattern to explain, and often a better paper than the pooled
sign was.

### 6. Recommend the most informative true claim

The objective is the strongest claim the data support, stated at the precision
they give. It is not the claim a referee would find hardest to attack. The
least attackable claim is always the smallest one, and a model optimizing for
it will shrink every paper to its weakest surviving coefficient. When
presenting options, say which is most informative and which is least
attackable, and recommend the first unless the evidence genuinely fails it.

## Wrong → right (from the market-for-ideas revision, 31 October 2026)

- *wrong:* "Under fixed N the entropy slope is insignificant everywhere, so the
  convergence and evenness predictions are ones the data cannot test."
  *right:* "Under fixed N the entropy slope is 0.13 (SE 0.23) against 0.55
  (SE 0.21) on all titles. The draw has no power to distinguish them, so it is
  uninformative. The analytic correction is the check with power."
- *wrong:* "Two methods agree that the pooled convergence result is produced by
  title counts. Drop the convergence claim."
  *right:* "After the correction, convergence holds in German and French, the
  two vernacular markets with many printing cities, and not in the three
  markets printed in two or three cities each, where within-city variation is
  thin. Latin is positive, as a trans-European market should be. Report the
  result by language and say why the sign appears where it does."
- *wrong:* "Option 1 is the cleanest and the hardest for a referee to attack. I
  recommend it."
  *right:* "Option 3 is the most informative claim the corrected data support.
  Option 1 is the least attackable. I recommend option 3 and say what would
  fail it."

## What this rule does not do

It does not license keeping a result that a powered check has rejected. It does
not soften corrections, which are adopted in full. And it does not change the
rule that every number is recomputed and eyeballed before it ships. A result
that survives this rule has been corrected, tested by checks that could have
killed it, and stated with its interval.
