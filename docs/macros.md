---
title: Macros
parent: RTRA SAS Program Guide
layout: default
created_date: 2020-06-02
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 4
---
## MACROS

**RTRAFreq** gives the weighted count of observations at each level of the *Class* variable(s). This procedure is appropriate for discrete variables because a *Class* variable cannot have more than 500 distinct values – as per the RTRA system limitation. The first row of the output table is the total weighted count without breaking it down by the *Class* variable. With every additional variables, a new variable column is added and a count for each combination of levels is given. The image below shows the output tables from the frequency procedure using one *Class* variable (left) and two *Class* variables (right).

![]({{ '/assets/images/RTRA_SAS_1.png' | relative_url }})

**RTRAPercentDist** gives the relative frequency or percentage of observations at each level or combination of levels of the *Class* variable(s). When more than one *Class* variable is specified, this procedure is equivalent to cell and marginal percentages in a 2x2 frequency table. The weighted count is also provided.

**RTRAProportion** gives, within each respective category of the *Class* variable(s), the percentage of observations at each level of the *ByVar* variable. The *Class* variable is the grouping variable. This procedure is equivalent to row and/or column percentages in a 2x2 frequency table. The weighted count is also provided.

The image below shows the output tables from the PercentDist procedure (left) and the Proportion procedure (right).

![]({{ '/assets/images/RTRA_SAS_2.png' | relative_url }})

**RTRAMean** provides the mean or what is commonly known as the average of the *AnalysisVarList* variable at each level of the *Class* variable.  If more than one *Class* variable is specified, it gives the mean of the *AnalysisVarList* variable at each combination of levels of the *Class* variables. The weighted count is also provided.

**RTRAPercentile** gives the value of the *AnalysisVar* variable below which a certain percent of observations fall (i.e., the Nth percentile of the *AnalysisVar* variable) for each level of the *Class* variable.  You cannot run this procedure without a *Class* variable. You can choose 3 percentiles to calcualte from the following list: 1, 5, 10, 20, 25, 30, 40, 50, 60, 70, 75, 80, 90, 95, 99. The weighted count is also provided.

The image below shows the output tables from the Mean procedure (left) and the Percentile procedure (right).

![]({{ '/assets/images/RTRA_SAS_3.png' | relative_url }})

**RTRARatio** gives the ratio of the totals of two continuous variables (*NumeratorVar* and *DenominatorVar*) at each level of the *ByVar* variable. When a *Class* variable is added, the ratio is given for each combination of the *Class* and *ByVar* variables. The weighted count is also provided.

**RTRAShare** gives a percentage which is the subtotal (sum) of the *Share* variable at each level of the *ByVar* variable divided by the grand total of the *Share* variable: the share of the *Share* variable at each level of the *ByVar* variable. When a *Class* variable is added, the shares are calculated at each level of the *Class* variable. The shares add up to 100% within each level of the *Class* variable. The weighted count is also provided.

Higher-order statistics can be calculated using modified versions of these procedures. You can learn more about such procedures [here](https://www.statcan.gc.ca/en/microdata/rtra/training/programming).

**Technique:** [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)