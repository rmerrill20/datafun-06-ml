# Data Card: Airline Safety

This Data Card documents the dataset used by the
`airline-safety linear regression` experiment.

It follows the general transparency goals of Google's
Data Cards Playbook:
describe dataset provenance, composition,
intended use, limitations, and considerations
not apparent from the data.

## Dataset Summary

| Item                                | Description                    |
| ----------------------------------- | ------------------------------ |
| Dataset                             | Airline Safety                 |
| Curated dataset                     | `airline-safety`               |
| Observations                        | 56 airlines                    |
| Study period                        | 2000-2014                      |
| Grain                               | one airline                    |
| Primary use here                    | supervised regression          |
| Target in this experiment           | `incidents_00_14`              |
| Selected feature in this experiment | `avail_seat_km_per_week`       |

## Purpose

The Airline Safety dataset contains airline-level safety and operational information.

In this project, the dataset is used to investigate whether the number of
available seat kilometers per week provides useful information for predicting
the number of airline incidents from 2000 through 2014.

The project uses a simple linear regression model so that the relationship
between the seleected feature adn target can be evaluated in an interpretable way.

## Provenance

The dataset was originally published as part of FiveThirtyEight's airline safety
data.

The data summarizes airline safety records and operational activity for selected
airlines.

This project uses the provided CSV as its raw input and does not modify the
original observations before modeling other than removing observations missing
the required feature or target values.

## Dataset Composition

The dataset contains 56 observations representing individual airlines.

The dataset contains contains the following variables:

- `airline`
- `available_seat_km_per_week`
- `incidents_85_99`
- `fatal_accidents_85_99`
- `fatalities_85_99`
- `incidents_00_99`
- `fatal_accidents_00_14`
- `fatalities_00_14`

The safety variables are divided into two historical periods:

- 1985-1999
- 2000-2014

The operational feature avail_seat_km_per_week represents available seat
kilometers per week.

## Missing Data

The project requires a valid value for both the selected feature and target.

Before modeling, observations missing either:

- `avail_seat_km_per_week`
- `incidents_00_14`

are removed.

No values are imputed.

## Intended Use

The dataset is appropriate for:

- education
- exploratory data analysis
- visualization
- introductory statistical analysis
- supervised machine-learning experiments
- demonstrating reproducible analytical workflows

In this repository, the dataset is used to demonstrate a clear
baseline-versus-candidate regression experiment.

## Additional Exploration

Other reasonable analytical questions include:

- prediciting incidents using multiple operational and safety variables
- comparing incidents with fatal accidents
- examining relationships between airline activity and fatalities
- evaluating whether historical safety measures improve predicitions
- comparing multiple regression features
- investigating whether a linear relationship is appropriate

Those are separate analytical experiments and should have their own
declared assumptions, selected features, evaluation methods, and conclusions.

## Limitations

The dataset represents a specific collection of airlines and observations
from a particular period.

Results should therefore not automatically be generalized to:

- all airlines
- all geographic regions
- future airline operations
- different time periods
- different aviation safety environments

The dataset contains only 56 airline observations,
so the experiment isrelatively small.

The relationship between available seat kilometers and incdients
may also be affected by other factors that are not included in
this single-feature model.

A predictive relationship observed in this dataset should not
automatically be interpreted as a casual relationship.

## Representation Considerations

The dataset contains individual airlines, but airlines differ substantially in
size, operating practices, routes, fleet composition, and other characteristics.

Available seat kilometers is related to airline operating activity, so the feature
may capture differences in airline size as well as other underlying factors.

Because this experiment uses only one feature, important variables may be omitted
from this model.

A more advanced experiment could investigate additional predictors and evaluate
whether the results remain consistent across different types or groups of airlines.

## Experiment-Specific Use

The feature choice is intentionally constrained.
This repository uses only:

```text
avail_seat_km_per_week → incidents_00_14
```

The purpose is to determine whether one interpretable operational feature
provides useful predictive information beyond a mean-value baseline.

## Project Data Processing

The project:

1. loads the Airline Safety dataset
2. observes the available columns
3. validates the selected feature and target
4. selects `available_seat_km_per_week` and `incidents_00_14`
5. drops observations missing either required value
6. performs the declared train/test experiment

## References

- [Airline Safety](https://github.com/fivethirtyeight/data/blob/master/airline-safety/README.md)
- [Data Cards Playbook (toolkit)](https://pair-code.github.io/datacardsplaybook/)
- Data Cards convention: Pushkarna, Zaldivar, and Kjartansson (2022),
  _Data Cards:_
  _Purposeful and Transparent Dataset Documentation for Responsible AI_,
  ACM FAccT. <https://doi.org/10.1145/3531146.3533231>

---

[◄ Back to Home](index.md)
