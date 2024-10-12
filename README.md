# Comparative efficacy and acceptability of pharmacological, psychological, and neurostimulatory interventions for attention-deficit/hyperactivity disorder in adults: a systematic review and component network meta-analysis

Each outcome-specific folder includes the related dataframe ([outcome] - df.rds) ready to be imported into the R environment as an rds file (R Data Serialization format) and analysed using the functions of the [netmeta](https://cran.r-project.org/web/packages/netmeta/index.html) package. Before running any analyses, please exclude non-eligible arms (e.g., df <- df[(df$eligibility==1),]).

## Summary of the key functions used
- netmeta() (e.g., netmeta(pw.df, ref = 'placebo'))
- discomb() (e.g., discomb(pw.df, ref = 'placebo'))
- netsplit() (e.g., netsplit(nma))

Details on these and other functions are included in the reference manual for [netmeta](https://cran.r-project.org/web/packages/netmeta/index.html) package.

### Example, continuous outcomes
- pw.c1 <- pairwise(treat = intervention, n = n, mean = mean, sd = sd, data = df1, studlab = id, sm = 'SMD')
- netmeta(pw.c1, sm = 'SMD', random = T, details.chkmultiarm = T, prediction = T, ref = nc.ref) # set nc.ref as “placebo” or other references if preferred/available
- discomb(pw.c1, sm = 'SMD', random = T, details.chkmultiarm = T, prediction = T, ref = nc.ref, inactive = nc.inactive.c) # set nc.inactive.c as “no treatment” if present

### Example, binary outcomes
- pw.d1 <- pairwise(treat = intervention, n = n, event = r, data = data1, studlab = id, sm = 'OR')
- netmeta(pw.d1, sm = 'OR', random = T, details.chkmultiarm = T, prediction = T, ref = nc.ref) # set nc.ref as “placebo” or other references if preferred/available
- discomb(pw.d1, sm = 'OR', random = T, details.chkmultiarm = T, prediction = T, ref = nc.ref, inactive = nc.inactive.c) # set nc.inactive.c as “no treatment” if present

## Addendum
This information was added on 12-October-2024 as per request of The Lancet Psychiatry peer-reviewers.

## Lead
- Edoardo G. Ostinelli (@EGOstinelli)
- Andrea Cipriani (@andcipriani)
- Samuele Cortese