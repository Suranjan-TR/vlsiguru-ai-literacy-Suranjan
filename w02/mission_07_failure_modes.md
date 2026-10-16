# Mission 7 - Understand Why ML Systems Fail

## 1. Introduction

A Machine Learning (ML) model may perform well during testing but fail when used in the real world.

This can happen because of poor-quality data, incorrect labels, missing values, noisy observations, biased datasets, data leakage or changes in real-world conditions.

Human oversight is also important because incorrect predictions can have serious consequences.

## 2. Common Reasons Why ML Systems Fail

### A. Poor-Quality or Unrepresentative Data

A model learns from the examples provided to it. If the data contains errors or does not represent real-world situations, the model may learn incorrect patterns.

**Example:** A chip-timing model is trained using measurements from only one type of chip design but is later used on very different designs.

**Possible solution:** Collect reliable and representative data covering the intended use cases.

### B. Label Errors

A label is the known answer associated with a training example. If the label is incorrect, the model may learn the wrong relationship.

**Example:** A chip design that failed timing is incorrectly labelled as Pass.

**Possible solution:** Verify labels against reliable measurements and correct inconsistent or incorrect entries.

### C. Missing Values and Noisy Observations

Missing values occur when a feature has no recorded value. Noisy observations contain errors or unwanted variation.

**Example:** Some chip-design records have missing delay measurements, while others contain incorrect power readings because of measurement errors.

**Possible solution:** Investigate missing values, validate measurements and use an appropriate cleaning or imputation method.

### D. Data Bias

Data bias occurs when the available data systematically misrepresents the real-world situations the model is expected to handle.

**Example:** A model is trained mostly on one type of chip design and performs poorly on other design types.

Model performance can differ across subsets of data. A good overall score does not guarantee good performance for every group or condition.

**Possible solution:** Evaluate the model separately across relevant subsets, identify underrepresented cases and improve the data where needed.

### E. Data Leakage

Data leakage occurs when information that would not legitimately be available for prediction enters the training or evaluation process.

This can make evaluation results look better than the model's real-world performance.

**Example:** A model predicts whether a chip design will fail timing but uses a report field that is generated only after the timing test is completed.

The model may appear highly accurate because it indirectly receives information about the answer.

**Possible solution:** Use only features available at the time of prediction. Review the data preparation process and keep training, validation and test data appropriately separated.

### F. Changes in Real-World Data

Real-world data can change over time. A model trained on older data may become less reliable when the conditions it encounters change.

This is often called **data drift** or **distribution shift**, depending on what changes.

**Example:** A chip-timing model trained on older design processes performs poorly when a new process technology or design methodology is introduced.

**Possible solution:** Monitor incoming data and model performance, investigate changes and retrain or update the model when justified.

## 3. Three Hypothetical ML Failure Analyses

The following cases are hypothetical examples created for this assignment.

### Failure 1: Chip-Timing Model Misses Failing Designs

**Situation:**

A model predicts whether a chip design passes or fails timing. During testing, it appears accurate, but after deployment, several designs that fail timing are predicted as Pass.

**Likely cause:**

The training data contains incorrect timing labels, missing measurements or too few examples of failing designs.

**Evidence that could confirm the cause:**

- Compare the original labels with verified timing reports.
- Check how many failing examples are present in the training data.
- Inspect missing and unusual measurement values.
- Measure recall for the Fail class on recent, correctly labelled examples.

**Possible mitigation:**

Correct incorrect labels, investigate missing measurements and add representative failing examples. Evaluate the model using metrics that reflect the cost of missing a failure.

**Possible consequence:**

A failing design may be incorrectly accepted, causing additional debugging, redesign work or project delays.

### Failure 2: Model Performs Poorly on a Different Design Type

**Situation:**

A model predicts power consumption accurately for one type of chip design but produces poor predictions for another type.

**Likely cause:**

The training dataset is unrepresentative and contains too few examples of the second design type. The model may have learned patterns specific to the first type.

**Evidence that could confirm the cause:**

- Compare the types of designs represented in training and real-world data.
- Measure prediction errors separately for each design type.
- Check whether important features have different distributions between the two types.
- Review the data collection process for missing categories or conditions.

**Possible mitigation:**

Collect reliable examples from the underrepresented design type, evaluate performance separately for each type and validate the model before using it in the new setting.

**Possible consequence:**

Engineers may make incorrect power estimates and select a design that does not meet its power requirements.

### Failure 3: Model Looks Excellent in Testing but Fails After Deployment

**Situation:**

A model predicts whether a chip design passes timing with very high test accuracy. After deployment, its predictions are much less reliable.

**Likely cause:**

Data leakage may have allowed information generated after the timing test to enter the model's input features. Another possible cause is that real-world input data differs from the data used during evaluation.

**Evidence that could confirm the cause:**

- Review every input feature and determine when it becomes available.
- Check whether any feature directly or indirectly reveals the target answer.
- Re-evaluate the model after removing suspicious features.
- Compare training, test and production data distributions.
- Check whether the same feature-processing steps are used in testing and deployment.

**Possible mitigation:**

Remove leaked information, rebuild the data pipeline using only legitimate prediction-time features and evaluate on a separate dataset that represents real-world use. Monitor performance after deployment.

**Possible consequence:**

Engineers may trust misleading accuracy results and make design decisions based on unreliable predictions.

## 4. Human Oversight and Consequences of Incorrect Predictions

ML predictions should not automatically be treated as correct answers.

Human oversight is especially important when a prediction can affect safety, cost, reliability or engineering decisions.

For example, if an ML model predicts that a chip design will pass timing, engineers should still use the appropriate timing-analysis and verification processes before accepting the design.

Human oversight can include:

- Reviewing high-risk or uncertain predictions.
- Comparing predictions with established engineering checks.
- Investigating unusual results rather than automatically accepting them.
- Monitoring model performance after deployment.
- Correcting errors and feeding verified information back into the development process.

Human review does not guarantee that every error will be caught, but it can reduce the risk of relying blindly on incorrect predictions.

## 5. Summary Table

| Failure type | Likely cause | Evidence to investigate | Possible mitigation |
|---|---|---|---|
| Incorrect timing predictions | Incorrect labels or poor-quality data | Verified timing reports and data-quality checks | Correct labels and improve data quality |
| Poor performance on a design type | Unrepresentative or biased training data | Performance metrics by design type | Collect representative data and evaluate subsets |
| Excellent testing but poor deployment | Data leakage or changed real-world inputs | Feature availability and training-versus-production comparisons | Remove leaked features and monitor deployed performance |

## Conclusion

ML systems can fail even when their initial evaluation looks good. Poor-quality data, label errors, missing values, data bias, leakage and changing real-world conditions can all reduce reliability.

Investigating a failure requires evidence, not just guesses. Engineers should examine the data, measure performance across relevant subsets and verify that the model receives only appropriate inputs.

Human oversight, reliable testing and ongoing monitoring help reduce the consequences of incorrect predictions.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
