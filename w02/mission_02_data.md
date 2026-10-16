# Mission 2 - Understand Data: What Does an ML System Learn From?

## 1. Important Data Concepts

| Concept | Explanation | Example |
|---|---|---|
| Dataset | A collection of related data used for analysis or machine learning. | Measurements from multiple chip-design runs. |
| Sample | One example included in a dataset. | Data from one chip-design run. |
| Observation | A recorded instance of something measured or observed. | The delay measured in one design run. |
| Feature | An input variable used by a model to make a prediction. | Clock frequency or cell area. |
| Label | The known answer or category associated with a sample. | Timing pass or timing fail. |
| Target | The outcome the model is intended to predict. | Whether a design run passes timing. |

A dataset contains multiple samples or observations. Features describe each sample, while a label or target provides the known outcome when the task is supervised learning.

## 2. Structured and Unstructured Data

### Structured Data

Structured data is organised into a defined format, such as rows and columns in a table.

**Example:** A table containing clock frequency, cell area, delay, and timing status for different chip-design runs.

### Unstructured Data

Unstructured data does not follow a simple, fixed tabular format.

**Example:** Simulation log files, design documentation, and engineering reports.

## 3. Numerical and Categorical Features

| Feature Type | Explanation | Example |
|---|---|---|
| Numerical | Represents a measurable or countable quantity. | Clock frequency, cell area, and delay. |
| Categorical | Represents a category or group. | Design type, process corner, or operating mode. |

Numerical features can be used as measured quantities, while categorical features represent distinct groups or classes.

## 4. Labelled and Unlabelled Data

### Labelled Data

Labelled data contains examples with known outcomes. It can be used in supervised learning.

**Example:** Historical chip-design measurements where each run is marked as either `Pass` or `Fail`.

### Unlabelled Data

Unlabelled data contains input information without a supplied target answer.

**Example:** Chip-design measurements containing frequency, area, and delay but no timing pass/fail status.

A model can use unlabelled data to explore patterns or group similar observations, depending on the learning approach.

## 5. Illustrative Dataset

The following is a **synthetic dataset created for learning purposes**. These values are illustrative and are not measurements from a real chip.

The goal is to predict whether a design run passes timing based on its clock frequency, cell area, and measured delay.

| Sample | Clock Frequency (MHz) | Cell Area (µm²) | Delay (ns) | Timing Status |
|---|---:|---:|---:|---|
| 1 | 100 | 800 | 7.2 | Pass |
| 2 | 125 | 850 | 7.8 | Pass |
| 3 | 150 | 900 | 8.5 | Pass |
| 4 | 175 | 950 | 9.4 | Fail |
| 5 | 200 | 1000 | 10.2 | Fail |
| 6 | 225 | 1100 | 11.0 | Fail |

### Identifying Features and Target

- **Dataset:** The complete six-row table.
- **Sample / observation:** One row representing one illustrative design run.
- **Features:** Clock frequency, cell area, and delay.
- **Target / label:** Timing status (`Pass` or `Fail`).
- **Task type:** Classification, because the model predicts a category.

For a real design, the timing status would need to be determined using the relevant timing constraints and analysis results. The synthetic values above are only examples and do not establish a universal relationship between frequency, area, delay, and timing status.

## 6. Data Collection and Cleaning

### Data Collection

Data collection means gathering relevant information from suitable sources.

For a chip-design project, data could come from historical design runs, timing reports, power reports, and area reports.

### Data Cleaning

Data cleaning means identifying and correcting or handling problems in the collected data before using it.

Examples include:

- Removing duplicate records.
- Checking that units are consistent.
- Correcting invalid values when the correct values can be established.
- Handling missing measurements.
- Investigating inconsistent labels.

## 7. Common Data Quality Problems

### Missing Values

A missing value occurs when a required measurement or field is unavailable.

**Example:** A design run has no recorded delay value.

If missing values are ignored or handled incorrectly, the model may learn from incomplete information or produce unreliable predictions.

### Noisy Data

Noisy data contains unwanted variation, measurement errors, or other inaccuracies.

**Example:** A delay measurement is recorded incorrectly because of a measurement or reporting error.

Noise can make it harder for a model to identify the actual relationship between the features and the target.

### Inconsistent Labels

Inconsistent labels occur when similar examples are assigned incorrect or conflicting outcomes.

**Example:** A design run that fails the specified timing requirement is mistakenly labelled `Pass`.

Incorrect labels can teach a supervised model the wrong relationship and reduce its predictive performance.

## 8. Why More Data Does Not Always Mean Better Data

Having more data does not automatically produce a better model. The data must also be accurate, relevant, representative, and consistently labelled.

For example, collecting thousands of design runs with incorrect delay measurements or wrong timing labels may produce a less reliable model than using a smaller, carefully checked dataset.

### Two Ways Data Quality Can Affect a Model

**1. Missing or inaccurate measurements**

If important delay values are missing or incorrect, the model may fail to learn the relationship between the input features and timing outcomes. This can lead to incorrect predictions for new design runs.

**2. Incorrect or inconsistent labels**

If timing pass/fail labels are wrong, the model may learn incorrect patterns. Even when its predictions appear accurate on the same flawed data, it may perform poorly on correctly labelled, unseen design runs.

## Conclusion

I learned that machine learning depends on data containing useful features and, for supervised learning, reliable target labels. Data collection and cleaning are important because missing values, noise, and incorrect labels can affect model performance. I also learned that the quantity of data alone does not guarantee quality or accurate predictions.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
