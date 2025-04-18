{% assign id = {{include.id}} %}
<!--Begin Generated Intro Tag (DO NOT REMOVE)-->
### Mandatory Data Elements and Terminology
The following data-elements are mandatory (i.e data MUST be present).

**Each {{site.data.structuredefinitions.[id].type}} Must Have:**
1. period.start: Starting time with inclusive boundary
2. group.stratifier.stratum.component.code: What stratifier component of the group
3. status: complete \| pending \| error
4. type: individual \| subject-list \| summary \| data-collection
5. period.end: End time with inclusive boundary, if not ongoing
6. date: When the report was generated. Note: The language in R5 was changed to calculated.  We are clarifying that intent.
7. group: Measure results for each group
8. group.stratifier.stratum.component.value: The stratum component value, e.g. male
9. period: What period the report covers
10. measure: What measure and version was calculated
11. reporter: Organization that generated the MeasureReport

**Each {{site.data.structuredefinitions.[id].type}} Must Support:**
1. description: Description of the population
2. countQuantity: Count as a Quantity
3. supplementalData: Supplemental Data
4. group.population: The populations in the group
5. group.stratifier.stratum.population.code: initial-population \| numerator \| numerator-exclusion \| denominator \| denominator-exclusion \| denominator-exception \| measure-population \| measure-population-exclusion \| measure-observation
6. group.population.count: Size of the population
7. scoring: proportion \| ratio \| continuous-variable \| cohort \| composite
8. group.stratifier.stratum.population.count: Size of the population
9. group: Measure results for each group
10. message: Evaluation messages
11. group.stratifier.stratum.value: The stratum value, e.g. male
12. group.code: Meaning of the group
13. strataltscoretype: Possible additional measureScore value types
14. group.population.code: initial-population \| numerator \| numerator-exclusion \| denominator \| denominator-exclusion \| denominator-exception \| measure-population \| measure-population-exclusion \| measure-observation
15. group.id: Unique id for inter-element referencing
16. group.stratifier.code: What stratifier of the group
17. description: Description of the stratifier
18. altscoretype: Possible additional measureScore value types
19. measurereport-category: What category is this measure report
20. group.stratifier.stratum: Stratum results, one for each unique value, or set of values, in the stratifier, or stratifier components
21. improvementNotation: increase \| decrease
22. calculatedDate: The date the score was calculated
23. groupImprovementNotation: increase \| decrease
24. description: Description of the group
25. group.stratifier: Stratification results
26. group.stratifier.stratum.population: Population results in this stratum
27. group.stratifier.stratum.measureScore: What score this stratum achieved

<!--End Generated Intro (DO NOT REMOVE)-->




**Additional Profile specific implementation guidance:**

{% include report-sd-imp-guidance.md %}

### Examples

{% include summary-measurereports.md %}

{% include link-list.md %}
