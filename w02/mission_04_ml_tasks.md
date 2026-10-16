# Mission 4 - Understand ML Task Types

## 1. Introduction

Machine Learning (ML) can solve different kinds of problems. The task type describes **what we want the model to do or predict**.

For example, a model may predict a category, estimate a numerical value, group similar data, or identify unusual observations.

The main ML task types are:

1. Classification
2. Regression
3. Clustering
4. Anomaly detection
5. Dimensionality reduction
6. Recommendation and ranking

## 2. Types of ML Tasks

### A. Classification

Classification predicts a category or class.

**Example:** Predicting whether a chip design passes or fails timing.

- **Input:** Clock frequency, cell area and measured delay.
- **Output:** Pass or Fail.

Other examples include spam detection and identifying whether a medical scan shows a particular condition.

### B. Regression

Regression predicts a numerical value.

**Example:** Predicting the delay of a chip design.

- **Input:** Clock frequency, cell area and other design measurements.
- **Output:** Predicted delay, such as 8.5 ns.

Other examples include predicting house prices and estimating electricity consumption.

### C. Clustering

Clustering groups similar data points without requiring predefined group labels.

**Example:** Grouping similar chip-design runs based on their power, performance and area measurements.

- **Input:** Power, performance and area measurements from different design runs.
- **Output:** Groups of similar design runs.

Other examples include grouping customers according to purchasing behaviour and grouping similar documents.

### D. Anomaly Detection

Anomaly detection identifies observations that differ significantly from normal patterns.

**Example:** Identifying an unusual power measurement during chip testing.

- **Input:** Power measurements collected from chip-testing runs.
- **Output:** An indication of whether a measurement is unusual.

Other examples include detecting unusual bank transactions and identifying abnormal sensor readings.

An unusual observation is not automatically an error. It may require further investigation.

### E. Dimensionality Reduction

Dimensionality reduction reduces the number of variables used to represent data while attempting to preserve useful information.

**Example:** Reducing hundreds of chip-design measurements into a smaller set of values for visualisation.

- **Input:** A dataset containing many features, such as power, delay, area and other design measurements.
- **Output:** A smaller representation of the data with fewer dimensions.

Other examples include simplifying high-dimensional image data and visualising complex datasets.

### F. Recommendation and Ranking

Recommendation suggests relevant items, while ranking orders items according to their relevance or another chosen criterion.

**Example:** Recommending suitable technical learning resources to a student.

- **Input:** The student's interests, previous activity and available resources.
- **Output:** Recommended resources or a ranked list of resources.

In a semiconductor context, a system could rank candidate design configurations according to predicted performance, power and area.

## 3. Real-World Problems Classified by Task Type

The following table contains eight illustrative examples, including four semiconductor-related examples.

| No. | Real-world problem | Task type | Input data | Expected output |
|---|---|---|---|---|
| 1 | Predict whether a chip design passes timing | Classification | Design measurements and timing-related features | Pass or Fail |
| 2 | Predict the delay of a chip design | Regression | Design features and historical measurements | Predicted delay in ns |
| 3 | Group similar semiconductor design runs | Clustering | Power, performance and area measurements | Groups of similar runs |
| 4 | Detect unusual power measurements during chip testing | Anomaly detection | Power readings from testing | Normal or flagged as unusual |
| 5 | Estimate house prices | Regression | Location, size and property features | Predicted house price |
| 6 | Identify spam emails | Classification | Email text and other relevant features | Spam or Not Spam |
| 7 | Simplify a dataset containing hundreds of features | Dimensionality reduction | High-dimensional feature data | A lower-dimensional representation |
| 8 | Recommend learning resources to a student | Recommendation/ranking | Interests, previous activity and available resources | Suggested or ranked resources |

These examples illustrate possible uses of ML. The expected outputs depend on how each problem is defined and what data is available.

## 4. Task Type vs. Learning Paradigm

A **task type** describes what the model is expected to do. A **learning paradigm** describes the kind of training signal or feedback used to learn.

| Point | Task type | Learning paradigm |
|---|---|---|
| Main question | What problem should the model solve? | How does the model learn? |
| Examples | Classification, regression, clustering | Supervised, unsupervised, reinforcement learning |
| Describes | The desired result | The learning process |

For example, consider predicting whether a chip design passes timing.

- **Task type:** Classification, because the output is a category: Pass or Fail.
- **Learning paradigm:** Supervised learning, if the model is trained using historical examples with known timing results.

Now consider grouping similar chip-design runs.

- **Task type:** Clustering, because the goal is to discover groups of similar runs.
- **Learning paradigm:** Unsupervised learning, if the model discovers these groups from data without predefined group labels.

Therefore, task type and learning paradigm are related, but they are not the same thing.

## 5. Can Different Algorithms Solve the Same Task?

Yes. More than one algorithm can address the same ML task. The choice depends on the dataset, the problem requirements, computational cost and how well the model performs.

| Task type | Possible algorithms or methods |
|---|---|
| Classification | Logistic regression, decision trees, support vector machines |
| Regression | Linear regression, decision tree regression, random forest regression |
| Clustering | K-means, hierarchical clustering, DBSCAN |
| Anomaly detection | Isolation Forest, Local Outlier Factor, statistical thresholding |
| Dimensionality reduction | Principal Component Analysis (PCA), autoencoders |
| Recommendation/ranking | Collaborative filtering, content-based recommendation, learning-to-rank methods |

These are examples of possible methods, not a statement that one algorithm is always best.

For instance, both logistic regression and decision trees can be used for classification. Their performance may differ depending on the data and the problem.

## 6. Important Points to Remember

- Classification predicts categories.
- Regression predicts numerical values.
- Clustering discovers groups of similar observations.
- Anomaly detection identifies unusual observations.
- Dimensionality reduction creates a representation with fewer dimensions.
- Recommendation suggests relevant items, while ranking orders items.
- A task type does not tell us by itself how the model was trained.
- Different algorithms can solve similar tasks.

## Conclusion

Machine Learning can address many kinds of problems, from predicting semiconductor timing results to detecting unusual measurements and recommending relevant information.

Choosing the correct task type starts with understanding the expected output. After defining the task, we can consider the available data, the learning paradigm and suitable algorithms.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
