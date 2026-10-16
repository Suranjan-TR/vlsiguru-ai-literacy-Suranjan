# Mission 6 - Understand Evaluation and Generalisation

## 1. Introduction

A Machine Learning (ML) model is useful only if it can make reliable predictions on data it has not seen before.

During training, a model learns patterns from examples. Evaluation helps us understand whether those patterns are useful beyond the training data.

Important concepts include training, validation and test datasets, generalisation, overfitting, underfitting and evaluation metrics.

## 2. Training, Validation and Test Datasets

A dataset is often divided into three parts for different purposes.

| Dataset | Purpose | Example |
|---|---|---|
| Training dataset | Used to teach the model by learning patterns from examples | Historical chip-design measurements used to learn a relationship |
| Validation dataset | Used during model development to compare models and tune settings | Measurements used to choose between different model configurations |
| Test dataset | Used for the final evaluation after model development | Separate measurements used to estimate how well the selected model performs on unseen data |

**Simple diagram:**

```text
             Complete dataset
                    |
          +---------+---------+
          |         |         |
          v         v         v
       Training  Validation   Test
          |         |         |
          v         v         v
       Learn     Tune and    Final
       patterns  compare     evaluation
                 models
```

The test dataset should be kept separate from model training and tuning. Repeatedly using test results to make development decisions can make the final evaluation less reliable.

## 3. Generalisation, Overfitting and Underfitting

### A. Generalisation

Generalisation is the ability of a trained model to perform well on new, unseen data from the relevant problem.

For example, a model trained on historical chip-design runs should make useful predictions for new design runs that were not included in its training data.

### B. Overfitting

Overfitting happens when a model learns the training examples too specifically, including noise or accidental patterns.

Such a model may perform very well on training data but poorly on unseen data.

**Example:** A model memorises patterns in historical chip-design measurements but fails to predict accurately for new designs.

### C. Underfitting

Underfitting happens when a model is too simple or has not learned enough to capture important patterns in the data.

It may perform poorly on both training data and unseen data.

**Example:** A model uses an overly simple relationship that cannot adequately represent the factors affecting chip delay.

### Comparison

| Concept | Training performance | Unseen-data performance |
|---|---|---|
| Good generalisation | Usually good | Usually good |
| Overfitting | Very good or much better | Often poor |
| Underfitting | Poor | Often poor |

## 4. Why Can Training Performance Differ From Unseen-Data Performance?

A model learns from the examples provided during training. Those examples may not represent every situation it will encounter later.

Performance can differ because:

- The model has memorised training examples instead of learning patterns that generalise.
- Training data contains noise, errors or incorrect labels.
- The training data does not represent the real-world cases the model encounters.
- New data has different characteristics from the training data.
- The model is too simple to learn the important relationships.

Therefore, high training performance alone does not prove that a model is useful. Evaluation on separate data is important.

## 5. Important Evaluation Metrics

Different metrics answer different questions. The right metric depends on the problem and the cost of different mistakes.

### A. Accuracy

Accuracy describes the proportion of all predictions that are correct.

**Question answered:** How often is the model correct overall?

A model can have high accuracy while missing an important minority class.

### B. Precision

Precision describes how many of the cases predicted as positive are actually positive.

**Question answered:** When the model predicts a positive result, how often is that prediction correct?

Precision is useful when false alarms are costly.

### C. Recall

Recall describes how many of the actual positive cases the model successfully identifies.

**Question answered:** Of all the actual positive cases, how many did the model find?

Recall is especially important when missing a positive case is costly.

### D. False Positives

A false positive occurs when the model predicts positive even though the actual answer is negative.

**Example:** A chip-testing model flags a design as faulty even though the design is not faulty.

### E. False Negatives

A false negative occurs when the model predicts negative even though the actual answer is positive.

**Example:** A chip-testing model marks a faulty design as acceptable.

### F. Absolute Error

Absolute error is the size of the difference between a predicted numerical value and the actual value, ignoring whether the prediction is higher or lower.

**Example:**

- Actual delay = 8 ns
- Predicted delay = 9 ns
- Absolute error = 1 ns

**Question answered:** How far is the numerical prediction from the actual value?

Absolute error is useful for regression problems, such as predicting chip delay.

## 6. Worked Example: Why Accuracy Can Be Misleading

Suppose a semiconductor testing dataset contains 1,000 chip-design runs:

- 990 runs pass testing.
- 10 runs fail testing.

A model predicts that **every run will pass**.

### Step 1: Count the predictions

| Actual result | Predicted Pass | Predicted Fail | Total |
|---|---:|---:|---:|
| Pass | 990 | 0 | 990 |
| Fail | 10 | 0 | 10 |
| Total | 1,000 | 0 | 1,000 |

The model correctly predicts all 990 passing runs. However, it misses all 10 failing runs.

### Step 2: Calculate accuracy

The model makes 990 correct predictions out of 1,000.

Accuracy = 990 / 1,000 = 99%

At first, 99% accuracy looks excellent.

However, the model has failed to identify even one faulty design.

### Step 3: Understand why accuracy is misleading

The dataset is **imbalanced** because passing runs are much more common than failing runs.

The model achieves high accuracy simply by always predicting the majority class, Pass.

If the purpose is to detect failing chip designs, this model is not useful despite its high accuracy.

### Step 4: Which additional metric is useful?

**Recall for the Fail class** is important because it measures how many actual failing runs the model identifies.

In this example:

- Actual failing runs = 10
- Failing runs correctly identified = 0
- Recall for Fail = 0 / 10 = 0%

The model identifies none of the failing runs.

This shows why recall can be more informative than accuracy when missing failures is costly.

Precision for the Fail class also matters when the model does predict Fail. In this example, the model makes no Fail predictions, so precision is undefined mathematically; some evaluation tools report it as zero by convention.

## 7. Why Compare Against a Simple Baseline?

A baseline is a simple method used as a reference point before deciding whether a more complex model is useful.

For example, if 99% of chip-design runs pass, a baseline that always predicts Pass achieves 99% accuracy.

A more complex model should be compared against this baseline using suitable metrics, such as recall for failing runs, not accuracy alone.

If the complex model achieves the same accuracy but identifies more failing runs, it may be more useful for the actual problem.

A baseline helps answer this question:

**Does the ML model provide a meaningful improvement over a simple approach?**

## 8. Choosing the Right Metric

| Problem | Useful metric | Reason |
|---|---|---|
| Detecting faulty chip designs | Recall for the Fail class | Helps measure how many actual failures are detected |
| Filtering spam emails | Precision, along with recall | Helps evaluate unwanted messages incorrectly flagged as spam and spam that is missed |
| Predicting chip delay | Absolute error | Shows the size of the numerical prediction error |
| General classification | Accuracy, when class balance and error costs make it appropriate | Summarises the proportion of correct predictions |

No single metric is best for every problem. The evaluation method should reflect the intended use of the model and the consequences of its mistakes.

## Conclusion

Evaluation helps determine whether an ML model has learned useful patterns and can generalise to unseen data.

Training, validation and test datasets have different roles. Overfitting and underfitting can reduce performance on new data. Metrics such as accuracy, precision, recall and absolute error answer different questions.

The worked example shows that 99% accuracy can still be misleading when the dataset is imbalanced. For detecting failing chip designs, recall for the Fail class provides important additional information. Comparing the model against a simple baseline also helps establish whether the model adds real value.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
