# Mission 2 - Understand Data: What Does an ML System Learn From?

## 1. Important Data Concepts

| Concept | Explanation | Example |
|---|---|---|
| Dataset | A collection of related data used for analysis or machine learning. | Measurements from multiple simulation runs. |
| Sample | One example included in a dataset. | Data from one simulation run. |
| Observation | A recorded instance of something measured or observed. | The functional coverage measured after one simulation run. |
| Feature | An input variable used by a model to make a prediction. | Test configuration or coverage before a simulation run. |
| Label | The known answer or category associated with a sample. | Whether a simulation run found a new coverage point. |
| Target | The outcome the model is intended to predict. | The amount of new functional coverage gained from a simulation run. |

A dataset contains multiple samples or observations. Features describe each sample, while a label or target provides the known outcome when the task is supervised learning. In some contexts, the terms label and target are used interchangeably.

## 2. Structured and Unstructured Data

### Structured Data

Structured data is organised into a defined format, such as rows and columns in a table.

**Example:** A table containing simulation configuration, test parameters, coverage before a run and coverage after a run.

### Unstructured Data

Unstructured data does not follow a simple, fixed tabular format.

**Example:** Simulation log files, verification reports, error messages and engineering documentation.

Structured data is generally easier to organise into a table, while unstructured data may need additional processing before it can be used by an ML system.

## 3. Numerical and Categorical Features

| Feature Type | Explanation | Example |
|---|---|---|
| Numerical | Represents a measurable or countable quantity. | Number of tests run, coverage percentage and simulation runtime. |
| Categorical | Represents a category or group. | Test type, operating mode or transaction type. |

Numerical features represent quantities, while categorical features represent distinct groups or classes.

## 4. Labelled and Unlabelled Data

### Labelled Data

Labelled data contains examples with known outcomes. It can be used in supervised learning.

**Example:** Historical simulation runs containing test configurations and the amount of new functional coverage gained from each run.

The known coverage gain can act as the target for a model that predicts how useful a new test configuration may be.

### Unlabelled Data

Unlabelled data contains input information without a supplied target answer.

**Example:** Simulation records containing test configurations and other measurements, but without a recorded coverage gain or outcome label.

A model can use unlabelled data to explore patterns or group similar observations, depending on the learning approach.

## 5. Illustrative Dataset

The following is a synthetic dataset created for learning purposes. These values are illustrative and are not results from a real verification project.

The goal is to predict the additional functional coverage that may be gained from a simulation run.

| Sample | Tests Run | Coverage Before (%) | Coverage After (%) | New Coverage Gained (%) |
|---|---:|---:|---:|---:|
| 1 | 100 | 60 | 65 | 5 |
| 2 | 100 | 65 | 67 | 2 |
| 3 | 100 | 67 | 75 | 8 |
| 4 | 100 | 75 | 76 | 1 |
| 5 | 100 | 76 | 82 | 6 |
| 6 | 100 | 82 | 85 | 3 |

### Identifying Features and Target

- **Dataset:** The complete six-row table.
- **Sample / observation:** One row representing one illustrative simulation run.
- **Features:** Tests run and coverage before the simulation run.
- **Target:** New functional coverage gained, calculated as coverage after the run minus coverage before the run.
- **Task type:** Regression, because the model predicts a numerical value.

For example, Sample 1 starts at 60% coverage and finishes at 65%, giving a coverage gain of 5 percentage points.

In a real verification project, the data would need to be collected from simulation results and checked for consistency. The useful features would depend on the goal. For example, test configuration, sequence type, constraints and previous coverage results could help describe a simulation run.

The table is only an illustration. It does not prove that a particular test configuration will produce a specific coverage gain.

## 6. Data Collection and Cleaning

### Data Collection

Data collection means gathering relevant information from suitable sources.

For a Design Verification project, data could come from:

- Simulation run summaries.
- Test and sequence configurations.
- Functional coverage reports.
- Simulation runtime measurements.
- Test pass/fail results.
- Verification logs and reports.

The collected data should be relevant to the prediction goal.

### Data Cleaning

Data cleaning means identifying and correcting or handling problems in the collected data before using it.

Examples include:

- Removing duplicate records when they do not represent separate valid observations.
- Checking that units and measurement formats are consistent.
- Correcting invalid values when the correct values can be established.
- Handling missing measurements.
- Investigating inconsistent labels or coverage results.

Cleaning should preserve valid information rather than removing data without understanding the reason for the problem.

## 7. Common Data Quality Problems

### Missing Values

A missing value occurs when a required measurement or field is unavailable.

**Example:** A simulation record contains the test configuration but has no recorded coverage result.

If missing values are ignored or handled incorrectly, the model may learn from incomplete information or produce unreliable predictions.

### Noisy Data

Noisy data contains unwanted variation, measurement errors or other inaccuracies.

**Example:** A simulation summary contains an incorrect runtime or an inaccurately recorded coverage percentage.

Noise can make it harder for a model to identify the actual relationship between the features and the target.

### Inconsistent Labels

Inconsistent labels occur when examples are assigned incorrect or conflicting outcomes.

**Example:** A simulation run that gained 5 percentage points of coverage is incorrectly recorded as having gained 2 percentage points.

Incorrect target values can teach a supervised model the wrong relationship and reduce its predictive performance.

## 8. Why More Data Does Not Always Mean Better Data

Having more data does not automatically produce a better model. The data must also be accurate, relevant, representative and consistently recorded.

For example, collecting thousands of simulation records with incorrect coverage measurements or inconsistent test configurations may produce a less reliable model than using a smaller, carefully checked dataset.

### Two Ways Data Quality Can Affect a Model

#### 1. Missing or Inaccurate Measurements

If important coverage measurements are missing or incorrect, the model may fail to learn the relationship between test configurations and coverage gains. This can lead to incorrect predictions for new simulation runs.

#### 2. Incorrect or Inconsistent Target Values

If coverage gains are recorded incorrectly, the model may learn the wrong patterns. Even if its predictions appear accurate on flawed data, it may perform poorly on correctly recorded, unseen simulation runs.

## 9. Connection to Design Verification

As a Design Verification learner, I can relate ML data to simulation results, test configurations and functional coverage measurements.

For example, an ML model could potentially help predict which test configurations are likely to produce additional functional coverage. This may help verification engineers prioritise simulations.

However, the model's predictions must be evaluated using actual simulation results. A predicted coverage gain does not prove that the test will find a design bug or that the design is fully verified.

Functional coverage measures which specified scenarios or coverage points have been exercised. It does not, by itself, prove that the design behaves correctly.

## Conclusion

I learned that machine learning depends on data containing useful features and, for supervised learning, reliable target values. Data collection and cleaning are important because missing values, noise and incorrect labels can affect model performance.

I also learned that the quantity of data alone does not guarantee quality or accurate predictions. In Design Verification, reliable simulation records and functional coverage measurements could help an ML model identify useful test patterns, but the predictions must be checked against actual verification results.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
