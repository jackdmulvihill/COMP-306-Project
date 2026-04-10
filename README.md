# COMP 306 Project by Denise Godinez and Jack Mulvihill
## Research Question
- **Given** the OpenAlex tables “Works” and “Works Authorships” provide information about
citation counts, authors, and the institution that published these works between 2020 and 2025.
- **Then** we aim to identify which institutions and combinations of institutions are most frequently
associated with highly cited research during this period.
- **How** we will approach this is by each highly cited paper we will look at the institutions
represented by its authors and analyze which institutions frequently appear together in impactful
research. Using frequent pattern mining we will identify recurring patterns and determine which
combinations are most associated with highly cited works.

## Primary Tables
- Works
- Works Authorships
- Works Topics

## Data Mining Method
- Frequent Pattern Mining

## Jack Mulvihill Progress
### Frequent Pattern Mining: Institutions Publishing Highly Cited Works and their Co-Authorship Patterns
- Created a new DataFrame **works_institutions** merging tables **Works** and **Works Authorships**
- Created a plot summing up total citations across all institutions and displaying the top ten institutions with most citations
- Map institution IDs to institution names
- Build a transaction <t, X> where each **work_id** is mapped to one or more **institution_id**
- Constructed a labeled TransactionEncoder where each **row** represents a **work** and each **column** is a **unique institution**
- Performed an Apriori search on multiple different MIN_SUPPORT thresholds
- Created a dual-panel plot plotting frequent itemsemsets found at various MIN_SUPPORT thresholds
- Mined frequent itemsets for frequent **solos**, **duos**, and **groups** of institutions publishing together
- Created plots plotting the supports of the most frequent solos, duos, and groups of institutions publishing together
- Generated association rules using **Jaccard** and **Kulczynski** as my primary means of evaluation
- Created a triple-panel plot plotting **Lift**, **Jaccard**, and **Kulczynski** scores against **Support** for generated rules
- Filtered rules for **1-1**, **1-N**, and **N-1** relationships of institutions frequently publishing together

## Denise Godinez's Progress 
### Frequent Pattern Mining: Research Sub-fields in Highly Cited Papers
- Created a new Dataframe **works_topics** merging tables **Works** and **Works Topics**
- Loaded highly cited works (published 2020-2025 with >100 citations)
- Inspected the distribution of **topic scores** to determine whether a score threshold was needed before building transactions
- Built a transaction <t, X> where each **work_id** is mapped to one or more **subfield_name** values
- Sampled 10,000 transactions for memory efficiency while preserving meaningful support values
- Constructed a labeled TransactionEncoder where each **row** represents a **work** and each **column** is a unique research subfield
- Performed an Apriori search across multiple **MIN_SUPPORT** thresholds to identify the best cut off
- Selected **MIN_SUPPORT = 0.01 (1% of papers)**, yielding **82 frequent itemsets**
- Generated **32 association rules** using **lift > 1.0** as the minimum threshold, filtering for above-chance co-occurrences
- Added symmetric metrics: **Cosine**, **Jaccard**, and **Kulczynski** to evaluate rules in both directions
- Created a horizontal bar chart of the **Top 15 most frequent subfields** in highly-cited papers, annotated with exact support values
- Created a bar chart of all **frequent subfield pairs**, showing combinations co-appearing in >1% of highly-cited papers
- Created a three panel scatter plot plotting **Confidence**, **Lift**, and **Kulczynski** scores against **Support** for all generated rules
- Created a final summary table of the top 15 rules ranked by Kulczynski, with a blue gradient highlighting the strongest lift and symmetry scores
