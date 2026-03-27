# BOTEC Writer

Build a back-of-the-envelope cost-effectiveness calculation following GiveWell's standard framework.

## When This Skill Applies

You need to produce a BOTEC for an intervention — either as a standalone analysis or as part of a QEA workflow.

## Inputs

- Intervention name and description
- Evidence gathered from literature search / paper reading
- (Optional) Existing GiveWell program to benchmark against

## Output

A markdown file with:
1. Revision log header (per review-loop protocol)
2. BOTEC summary (bottom line CE multiple, key drivers, confidence)
3. Full calculation walkthrough
4. Parameter table
5. Sensitivity analysis

Save to: `output/qeas/[intervention-name]-BOTEC.md`

---

## The 5-Question CEA Framework

Every BOTEC answers these five questions:

1. **Cost per person reached** — How much does it cost to deliver the program per beneficiary?
2. **Counterfactual coverage** — How much does the program *increase* coverage? (The counterfactual is usually NOT 0%!)
3. **Burden** — What is the baseline burden (mortality, morbidity) in the target population?
4. **Effect on burden** — How much does the intervention reduce the burden?
5. **Other effects** — What are other upsides (development effects, costs averted) and downsides (resistance, adverse effects)?

## Standard Calculation Steps

### Step 1: Start with $1,000,000 donation benchmark

| Parameter | How to estimate |
|-----------|-----------------|
| Drug/commodity cost | UNICEF supply catalogue, trial protocols, literature |
| Delivery/admin cost | Benchmark from similar GiveWell programs (e.g., SMC ~$5-10/child) |
| Total cost per child | Drug + delivery + overhead |

### Step 2: Beneficiaries Reached
```
Children reached = $1,000,000 / Cost per child
```
Discount for: coverage gaps, wastage, administrative overhead.

### Step 3: Counterfactual Coverage Adjustment
```
Children counterfactually reached = Children reached x (1 - Counterfactual coverage %)
```
**This is where most BOTECs go wrong.** The counterfactual is rarely 0%. Estimate what would happen without this specific donation.

### Step 4: Deaths Averted
```
Unadjusted deaths averted = Children CF reached x Baseline mortality x Relative risk reduction
```
Or equivalently: `Children CF reached x (1 / NNT)`

### Step 5: Internal and External Validity Adjustments

| Adjustment | Default | When to change |
|------------|---------|----------------|
| Internal validity | 90% | 95% for high-quality RCTs, 70-80% for observational |
| External validity | 90% | Lower for trial-to-implementation gap, different populations |

```
Adjusted deaths averted = Unadjusted x IV adjustment x EV adjustment
```

### Step 6: Initial CE Estimate
```
Total moral value = Deaths averted x 116 (moral value of under-5 life)
Moral value per dollar = Total moral value / $1,000,000
Initial CE multiple = Moral value per dollar / 0.0033545 (GiveWell cash benchmark)
```

### Step 7: Standard Adjustments

| Adjustment | Typical Range |
|------------|---------------|
| Lives saved over age 5 | +0-15% |
| Development effects | +5-25% |
| Additional benefits | +0-20% |
| Additional downsides | -0-10% |
| Leverage | -0-10% |
| Funging | -0-15% |

```
Net adjustment = (1+lives>5) x (1+development) x (1+benefits) x (1-downsides) x (1-leverage) x (1-funging)
Final CE multiple = Initial CE x Net adjustment
```

### Step 8: Sensitivity Analysis

| Scenario | Approach |
|----------|----------|
| Optimistic | Best-case for all key parameters |
| **Base case** | Central estimates |
| Conservative | Worst-case for key parameters |
| Very conservative | Pessimistic on ALL parameters simultaneously |

---

## Parameter Table Format

Every BOTEC must include this table:

```markdown
| Step | Parameter | Value | Source | Confidence |
|------|-----------|-------|--------|------------|
| 1 | Donation | $1,000,000 | Benchmark | -- |
| 2 | Cost per child | $X | [Author Year, Table N, p.X] | High/Med/Low |
| ... | ... | ... | ... | ... |
| 15 | **Final CE multiple** | **X x** | Calculated | -- |
```

---

## Source Documentation Requirements

**Every numerical parameter must have a specific source.** See `CLAUDE.md` for the full standard.

Prohibited:
- "Literature suggests..."
- "GBD data shows..."
- "Estimated from age patterns"

Required format:
- "Snow et al. 2020, Table 3, p.847: '5-9 year case fatality rate was 0.31% (95% CI: 0.28-0.34%)'"
- "IHME GBD 2021, Query: Cause=Malaria, Measure=Deaths, Age=5-9, Location=Mali, accessed [date]"

If you cannot find a number, say "I could not find data on X" and use a clearly marked placeholder with a range.

## Benchmarking

**Always benchmark against a similar GiveWell-funded program first**, then adjust with explicit rationale. For example:
- Malaria chemoprevention → benchmark off SMC costs
- Nutrition intervention → benchmark off vitamin A supplementation
- Water/sanitation → benchmark off chlorine dispensers

This catches implausible cost assumptions early.

## Interpretation Guide

| Final CE Multiple | Interpretation |
|-------------------|----------------|
| >15x | Highly cost-effective; strong candidate |
| 8-15x | Above GiveWell bar; warrants investigation |
| 4-8x | Near bar; may be competitive with uncertainties |
| 1-4x | Below bar; needs exceptional other factors |
| <1x | Not competitive; deprioritize |
