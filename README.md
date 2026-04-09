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
