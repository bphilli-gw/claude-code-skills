***Meta:***   
*The goal of this document is to create a guide to write QEA, with the aims of (a) sharing best practices across researchers and (b) bring future new researchers up to date more efficiently.*  
*This is work in progress. Feel free to add suggestions directly to the text or leave comments in any format you prefer.* 

## Questions for discussion

* See “Questions” section [here](https://app.asana.com/0/1199404148539837/list). 

## Ideas for improvements/things to add to this doc

* See “Tools” section [here](https://app.asana.com/0/1199404148539837/list). 

# Process

* **The big picture**
  * Time spent once training is completed: roughly 0.5-2 days for QEA.
  * Goal: decide whether to conduct further research.
  * Rough prioritization criterion: finding interventions that have a decent shot at being 8x+ and having high room for more funding

## Core CEA Framework (5 Questions)

Every cost-effectiveness analysis answers these five questions. Use this framework to structure your thinking and identify which parameters matter most:

1. **Cost per person reached** - How much does it cost to deliver the program per beneficiary?
2. **Counterfactual coverage** - How much does the program *increase* coverage? (Usually the counterfactual isn't 0%!)
3. **Burden** - What is the baseline burden (mortality, morbidity) in the target population?
4. **Effect on burden** - How much does the intervention reduce the burden?
5. **Other effects** - What are other upsides (development effects, costs averted) and downsides (resistance, adverse effects)?

## BOTEC-First Workflow

**Start with a BOTEC after reading the abstract only.** This helps you:
- Identify which parameters drive cost-effectiveness before deep research
- Focus evidence review on the parameters that actually matter
- Avoid spending time on questions that won't change the bottom line

Workflow:
1. Read abstract → Build initial BOTEC with rough guesses
2. Identify most sensitive parameters
3. Do targeted evidence review on those parameters
4. Update BOTEC → Check if bottom line changes
5. Iterate until you have sufficient confidence or hit a stopping point

* **Statement of the problem**
  * This section provides background on the problem; when possible, use quantitative information
  * Sources: WHO, [DCP-3](http://dcp-3.org/), CDC, background sections of academic papers on the intervention
  * The solution/program
  * The donation opportunity (if known) \[e.g. direct delivery, TA, adding a module to an existing platform\]
* **Evidence search**  
  * Sources: [Google Scholar](https://scholar.google.com/), [PubMed](https://pubmed.ncbi.nlm.nih.gov/), [Econ Papers](https://econpapers.repec.org/), [Cochrane CENTRAL](https://www.cochranelibrary.com/central)  
  * What to search for:   
    * Most up-to-date high-quality meta-analysis, and papers published since;  
    * If no meta-analysis:   
      * Keywords for the program \+ “trial”  
      * if there’s a paper prompting the QEA, search up and down citation trails (click cited by on Google scholar)  
* **Evidence review** (see [here](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.1i4wr8r2t62n) for details and examples)
  * How large is the body of evidence?
  * What type of studies are there?
  * How large is the sample size?
  * How large is the CI? Does it overlap with zero/one?
  * Check if control received any intervention
    * More broadly, think about the appropriate counterfactual for implementation and cost purposes
  * How closely does the outcome reported relate to our outcomes of interest?
  * For meta-analysis: are the results highly heterogeneous? Is there a clear reason why?

* **Counterfactual coverage (often neglected!)**
  * The counterfactual is usually NOT 0% coverage
  * Examples:
    * Without net campaigns, people could get nets from clinics or stores
    * Without vaccine incentives, some kids would get vaccinated anyway
    * Without MDA, some people would seek treatment when symptomatic
  * Ask: What would coverage be without this program? What's the *marginal* increase?

* **Internal validity assessment** - Did the treatment cause the observed effect in this setting?
  * Direct forms of bias:
    * RCT or observational evidence?
    * Baseline imbalance between treatment and control?
    * Spillover effects (did control group benefit from treatment group)?
    * Publication bias (positive results more likely to be published)?
    * Differential attrition (did dropouts differ between arms)?
    * Self-report bias (subjective vs. objective outcomes)?
  * Bayesian adjustments:
    * No specific reason for bias but effects seem implausibly high (or low)?
    * Deworming is canonical example - large effects warrant extra scrutiny
  * Be sure to explain direction - why are you adjusting up/down?

* **External validity assessment** - How likely is it the effect generalizes to the setting we'd fund?
  * Implementation quality:
    * Trial done at small scale with intense oversight vs. real-world implementation
    * Adherence in trial vs. likely real-world adherence
  * Changes in program components:
    * Lower drug dosage, different formulation, different delivery mechanism
    * SMS reminders vs. cash incentives vs. community health workers
  * Differences in disease burden:
    * Often account for this directly in the burden parameter
    * But consider: transmission intensity, resistance patterns, health system capacity, population characteristics  
* **Costs search/review**
  * **Primary approach: Benchmark off similar programs**
    * Best source is cost data from similar programs GiveWell has already investigated in depth
    * Example: For a new malaria chemoprevention program, start with SMC cost data and adjust
    * Don't spend excessive time on desk research - the best cost data comes from implementers
  * Secondary sources (if no benchmark available):
    * [Google Scholar](https://scholar.google.com/), [UNICEF supply catalogue](https://supply.unicef.org/)
    * Pull estimates from papers if available
  * Quick checks:
    * How does the program described in the costing analysis compare with the likely donation opportunities? Are there obvious components missing? Are there components that would not be relevant to donation opportunities?
    * Are there obvious reasons to believe costs in the literature might not be representative (e.g. drug costs have changed significantly since the study was conducted, different geographic contexts)?
    * How does the estimate from the literature compare with estimates for similar interventions in our CEA?
  * As a result of those checks, adjust by (a) giving more weight to sources that pass more checks or (b) give a subjective best guess of how those considerations might affect the cost.  
* **RFMF**
  * Estimate "total market" as: Cost \* (eligible population \- coverage)
    * Sources for eligible population/coverage: WHO, UNICEF
  * Does a quick Google search (\~15 mins) indicate whether there are known non-financial bottlenecks (e.g. supply, regulatory environment)?
  * Does a quick Google search indicate there are large funders supporting the program?
  * **Implementer Reality Check** (see detailed checklist below)  
* **Implementation Risk** (see [here](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.l47qg67ej4tt) for more details)  
  * Based on the evidence review  
    * How many steps does it take to solve the problem?  
      * Fewer steps (just give a treatment) \> more steps (test and *then* treat)   
    * Are there serious offsetting effects?  
      * E.g. increased fraud, negative spillovers    
    * What type of donation opportunities are we likely to find?  
      * More direct opportunities (e.g. paying for pills) \> less direct opportunities (e.g. technical assistance to set up a deworming program)  
  * Compare against other charities/programs in the [dashboard](https://docs.google.com/spreadsheets/d/1ETGNfjzDDGzAXeZ71Fh1fbz3IgXfBIGbIgCKtM7My-w/edit?ts=5fa4b0ab#gid=1441468168&range=A1).  
* **Implementation Maturity** (see [here](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.t16qda19ww1t) for more details)  
  * Does a quick Google search indicate there are organizationsorganisations working on this? If so, how many, in how many countries, and how large are the programs?   
  * Compare against other charities/programs in the [dashboard](https://docs.google.com/spreadsheets/d/1ETGNfjzDDGzAXeZ71Fh1fbz3IgXfBIGbIgCKtM7My-w/edit?ts=5fa4b0ab#gid=1441468168&range=A1).  
* **When to stop an investigation**  
  * Use criteria outlined in the prioritization [pipeline](https://docs.google.com/spreadsheets/d/1ETGNfjzDDGzAXeZ71Fh1fbz3IgXfBIGbIgCKtM7My-w/edit#gid=571799946)**,** and described in more detail [here](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.yz87o1laj8hs).   
* **Style**  
  * No need to make this formal: e.g. you can just include direct quotes, bullet-pointed lists are fine, not necessary to include page numbers with all citations, etc.  
* **Things to think about throughout**  
* Do the minimum work necessary to answer key questions / reach a conclusion.  
  * Prioritize areas which are likely to (i) lead to program deprioritization (ii) be quick to evaluate.  
* Tips  
  * Do a quick check on: strength of evidence, CEA; RFMF, and see if there’s a reason to deprioritize.  
  * Whenever thinking of next steps, try and identify discrete relatively high value 1-2h tasks \- it will almost always be worth doing those. 

# Checklist for QEAs

## What to include in a QEA	

**Bottomline (one paragraph summary of the summary)**

**Summary**

* How this fares in terms of the prioritization pipeline, for each criterion (e.g. low strength evidence, medium c-e, etc)

**What is the problem/program**

* Give a general statement of problem 	  
* Define intervention, including different components and target population beneficiaries

**What is the evidence of effectiveness**

* Describe search strategy  
  * Outcome variables you’re focusing on/why  
  * Databases searched/ keywords used  
* For each key piece of evidence   
  * Type of study  
  * Sample size  
  * Outcome measure: What is it? How does it relate to primary outcomes of interest (e.g., deaths, consumption)?  
  * Results (including CI)   
  * Adverse effects mentioned in the abstract  
  * For meta-analysis: heterogeneity, number of studies, countries  
* Overall strength of evidence for each of the key outcomes

**How cost-effective is it?**

* In the BOTEC, include  
  * Main benefits
    * Outcomes in absence of program / Baseline burden
      * Primary sources: [IHME GBD Results Tool](http://ghdx.healthdata.org/gbd-results-tool), [IGME](https://childmortality.org/) (for child mortality)
      * Papers themselves often have baseline rates in control groups
      * Consider adjustments for: age ranges (mortality highest in first month/year), self-selection (e.g., women attending ANC may have lower mortality)
    * Benefits from key outcomes  
  * Adjustments  
    * IV adjustment (default to 90% but adjust up or down based on any concerns about study quality)[^1]  
    * EV adjustment (default to 90% but adjust up or down based on any concerns about generalizability)[^2]  
    * If relevant  
      * Development benefits adjustment  
      * HouseholdHH income multiplier  
      * Adverse effects   
      * Other adjustments used in “core model” CEA (e.g., effect on transmission for malaria, indirect deaths averted)  
      * Adjustments for other benefits that are harder to directly model (e.g. morbidity)  
  * Costs  
    * Include costs for all philanthropic actors  
  * Result in multiples of cash/GiveDirectlyGD   
  * Sensitivity to major uncertainties  
    * E.g. lower/upper bounds on costs  
    * Demographics (e.g. check 2-4 countries where the burden is highest)  
* Include a brief summary of what’s driving cost-effectiveness: for example, the intervention is fairly expensive, but probability of death among the targeted group is high and effect size is moderate, leading to overall high cost-effectiveness. Also consider including a simple calculation of most important CEA inputs or how they compare to other “benchmark” CEAs.  
* (Tentative) Don’t include adjustments for (1) items in inclusion/exclusion, (2) downside adjustments and (3) leveraging/funging.[^3]

   
[**RFMF**](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.98ifscm2c2vd)

* Estimate RFMF as: Cost \* (eligible population \- coverage)
* Report whether there are known non-financial bottlenecks (e.g. supply, regulatory environment)

### Implementer Reality Check

Don't just estimate theoretical RFMF - verify that a delivery pathway actually exists. Spend 30-60 minutes searching for and documenting:

#### 1. Implementer Search (~20 mins)

Search for organizations currently working on this intervention or closely related interventions:
- Search terms: "[disease/condition] program Africa NGO", "[intervention] implementer organization", "[country] [disease] foundation"
- Check: WHO partner lists, Global Fund recipients, USAID implementing partners, foundation grantee lists

**Document in a table:**
| Organization | Countries | Current focus | Could deliver this intervention? |
|--------------|-----------|---------------|----------------------------------|
| ... | ... | ... | Yes/No/Uncertain - why |

#### 2. Gap Assessment

Answer these questions:
- **Are there organizations currently delivering this exact intervention?** (Best case)
- **Are there organizations delivering related interventions that could add this?** (Medium case - note integration challenges)
- **Would this require creating new programs from scratch?** (Worst case - significantly increases implementation risk)

#### 3. Pathway to Deployment

If no current implementers exist, what would be required?
- Policy/guideline changes (WHO, national)?
- New supply chains?
- Training programs?
- New organizational capacity?

Rate the pathway: **Clear** / **Plausible but uncertain** / **No clear pathway**

#### 4. Red Flags

Watch for these warning signs that RFMF may be overstated:
- The only "implementers" are the trial investigators themselves
- Related programs exist but focus on different interventions (integration may be harder than it seems)
- Guidelines recommend the intervention but no one actually delivers it
- Large theoretical target population but no infrastructure to reach them

#### 5. RFMF Summary Table

Include this in every QEA:

| Factor | Assessment |
|--------|------------|
| Funding gap exists? | Yes/No/Uncertain |
| Implementers exist for this specific intervention? | Yes/Partial/No |
| Could absorb funding at scale? | Yes/Uncertain/No |
| Non-financial bottlenecks? | List them |
| Pathway to deployment | Clear/Plausible/No clear pathway |

**Key principle**: A large theoretical funding gap with no implementers is worth less than a smaller gap with proven delivery channels.

[**Implementation maturity**](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.t16qda19ww1t)  
(TBD)

[**Implementation risk**](https://docs.google.com/document/d/1x9CtuMB5dn7J99bBS7bgPDMpDjE8Z-n0Jr-l2E1N2NY/edit#heading=h.l47qg67ej4tt)  
(TBD)

**Uncertainties**

* List main uncertainties in the review and communicate level of uncertainty for each  
* Things you didn’t do, if relevant

**Bottom line and next steps**

* Decide [promisingness of intervention](https://docs.google.com/spreadsheets/d/1ETGNfjzDDGzAXeZ71Fh1fbz3IgXfBIGbIgCKtM7My-w/edit#gid=571799946)  
* Recommend if deprioritize or keep investigating  
* If keep investigating: what uncertainties you’d prioritize and how they should be investigated (e.g. desk research vs experts interviews)

### Skeptical Checks (Pressure Testing)

After completing an initial QEA draft, run through these questions to identify overconfidence and hidden assumptions. The goal is to find the weakest links in your reasoning before others do.

#### Evidence Base Scrutiny

1. **Single study reliance**: Is the cost-effectiveness estimate primarily driven by one study? If so:
   - What would your estimate be if that study's effect size were 50% smaller?
   - Are there other studies testing similar interventions that found different results? Why might they differ?
   - Would the intervention still clear the bar if the key study were excluded?

2. **Publication bias**:
   - Is this a "positive" result that's more likely to be published than null findings?
   - Have you searched for unpublished trials, grey literature, or conference abstracts?
   - Are there registered trials that never published results?

3. **Comparator validity**:
   - What was the control group receiving? Is it truly representative of the counterfactual?
   - If comparing to "standard of care," is that standard actually failing, or is that the study authors' framing?
   - Has any authoritative body (WHO, Cochrane, etc.) endorsed the claim that current practice is inadequate?

#### External Validity Red Flags

4. **Trial-to-implementation gap**:
   - What was adherence in the trial vs. likely real-world adherence?
   - Were there intensive follow-up procedures that wouldn't exist at scale?
   - What percentage of the effect might be lost outside trial conditions? (Default: assume 20-40% loss)

5. **Context specificity**:
   - Were there features of the trial setting (transmission intensity, resistance patterns, health system capacity, population characteristics) that differ from target implementation settings?
   - Did other trials in different contexts find different results?

6. **Dosing/delivery differences**:
   - Would real-world implementation use the same drug formulation, dosing schedule, and delivery mechanism?
   - Are there supply chain, cold chain, or training requirements that might not transfer?

#### Cost Estimation Challenges

7. **Cost realism**:
   - Are your cost estimates from trial settings or actual program implementation?
   - Have you inflated costs by 25-50% to account for implementation realities?
   - Are there hidden costs (training, supervision, supply chain, monitoring) not captured?

8. **Scale effects**:
   - Do costs assume economies of scale that may not materialize?
   - Are there diseconomies of scale (harder-to-reach populations, weaker health systems) as programs expand?

#### Framing and Claims

9. **Strong claims audit**:
   - List every strong claim in your QEA (e.g., "SP is failing," "highly cost-effective," "substantial room for funding")
   - For each: What is the source? Is it the study authors' framing or independent consensus? Would a skeptical reader accept this claim?

10. **Counterfactual clarity**:
    - What happens without this intervention? Is the status quo actually as bad as claimed?
    - Are there alternative interventions that could address the same problem?

#### Quantitative Sanity Checks

11. **Effect size plausibility**:
    - Is the effect size unusually large compared to similar interventions?
    - If an 80% reduction, what's the biological/behavioral mechanism that makes this plausible?
    - GiveWell rule of thumb: effect sizes >50% warrant extra scrutiny

12. **NNT/cost-per-outcome check**:
    - Does the NNT assume trial-level adherence and follow-up?
    - What's the NNT under pessimistic assumptions (50% adherence, 70% of effect size)?

13. **Range testing**:
    - What's your cost-effectiveness estimate under pessimistic assumptions for all key parameters simultaneously?
    - Does it still clear the bar? If barely, downgrade confidence.

#### Pre-mortem Exercise

14. **Imagine the intervention fails at scale**. What are the three most likely reasons?
    - Adherence problems?
    - Context-specific effects that don't generalize?
    - Cost overruns?
    - Resistance/adaptation by disease or behavior?
    - Offsetting negative effects?

15. **What would change your mind?**
    - Specify what evidence would make you substantially revise your estimate downward
    - If you can't articulate this, you may be overconfident

#### Documentation

After running these checks, add a "Skeptical Assessment" section to your QEA that:
- Lists the 3-5 biggest concerns/uncertainties identified
- Provides adjusted estimates under pessimistic assumptions
- Explicitly states what evidence would change your conclusion

### Review Criteria

QEAs are evaluated on three dimensions:

**1. Legibility**
- Do you clearly state the bottom line, rationale, uncertainties, and next steps?
- Does the report make it clear what information you have based each statement on and how confident you are in each statement?
- Is the output easy to follow (both the QEA write-up and BOTEC spreadsheet)?
- Is the output concise, and does it only focus on main points?

**2. Technical Skills**
- Did you come up with a reasonable estimate of cost-effectiveness?
- Did you appropriately review the relevant empirical literature and make adjustments?
- Are there any major mistakes in calculations or reasoning?

**3. Productivity/Prioritization**
- Did you focus on the most important issues and move the rest to the side?
- Did you identify the most important uncertainties, not just a laundry list?
- Did you appropriately prioritize the next steps for the investigation (if any)?

### Useful resources

* [This](https://docs.google.com/spreadsheets/d/17NAfuDBENMAnQWRSSqVf1Z4xLifK0EDDpIJbBULlVhs/edit#gid=0) document gives a list of inputs that are expected to be included in the QEA vs IR vs grant CEA  
* General guidelines on [writing up research](https://docs.google.com/document/d/1dK_f3jREGRECfLDfRzBduTHghsi_ISZG3nqLXN5OvQ0/edit)  
* [Guide to GiveWell CEAs](https://docs.google.com/document/d/1ZKq-MNU-xtn_48uN33L6VvBEZRAduvjwWMeaEffL4K4/edit#heading=h.gt9hvkefg8aj)   
* [Moral weights tool](https://docs.google.com/spreadsheets/d/1YiZmHQb-JsDIDJF_tKKVte2x5NOL0CGUTndJNoB0iHo/edit#gid=0)  
* [Stephan’s guidance](https://docs.google.com/document/d/13HACIedT3oE8L8W361KwWQe4WLGbM7eJH_3gUY9eZ70/edit) on RCT searches

### QEA examples

* [Mindspark Education Technology QEA](https://docs.google.com/document/d/1ulma8M73x6zQxMn6OX_4OXX80AuwZSWKmSauKR6KuuQ/edit#heading=h.43glr7sy7vt6)   
* [Helping Babies Breathe (HBB) QEA](https://docs.google.com/document/d/1AXCc-DPIpiBClMrGsnz0tuegLbGFANSPeUbVdtzEXaI/edit#heading=h.yugtw9ghddmf)   
* [Salt substitution for hypertension QEA](https://docs.google.com/document/d/16N0sNIZno43GAShIxIc6Rilkvk4LyGIxtdJ-ZlJ-5rk/edit#heading=h.52cru8erbtji)  
* [Non-pneumatic anti-shock garment (NASG) QEA](https://docs.google.com/document/d/10ALE72O0VS6rkxrybbckYk_YBFNYAXnKdM0gAbobRBU/edit#heading=h.tp2wufljm7kr) 

To do

- Change place to resources  
- Make a guess on moral weights  
- When to look for further studies aside from meta-analysis  
- Ways of expressing uncertainties: 80% CI, GRADE style, % off, \# hours work the answer would be x times off either way.  
* 

[^1]:  Some guidance on things to look for is [here](https://docs.google.com/document/d/1pgFoKuYqDS5kGLvh7_XEjtFZ69oCkvfpHiuJ7DZ-2RA/edit).

[^2]:  Some guidance on things to look for are [here](https://docs.google.com/document/d/1kV6k6QuFS5VtJU__16IpWnouXPWMDgo-fc2OaZZ0-7U/edit).

[^3]:  Rationale: For (1) inclusion/exclusion, (2) downside adjustments, and (3) leveraging/funging, my initial inclination is not to make adjustments. Here's why: While there's wide variation across top charities, the average final cost effectiveness with all adjustments (i.e., w/ (1), (2) and (3)) is [20% higher](https://docs.google.com/spreadsheets/d/1mlFv887Nd8PiEqlDF-BMepEG3gUiLZ6ahQ4X4lWdGvc/edit#gid=1034883018&range=C27:D27) than the cost-effectiveness in the core model. If we exclude deworming (which gets a big boost from leveraging), it's [10% lower](https://docs.google.com/spreadsheets/d/1mlFv887Nd8PiEqlDF-BMepEG3gUiLZ6ahQ4X4lWdGvc/edit#gid=1034883018&range=C28:D28). Given how much uncertainty we'll have on (1), (2) and (3) at the QEA stage, it doesn't seem like we'll know enough to veer much from a base rate of \-10% to \+20%. Maybe in some cases we'll have a sense that funging will be a big concern or the downside adjustments will be large, for example, but it seems like this will be rare.