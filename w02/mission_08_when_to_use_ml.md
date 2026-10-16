# Mission 8 - Does This Problem Actually Need ML?

## 1. Introduction

Machine Learning (ML) is not the best solution for every problem. Sometimes a fixed rule or a conventional program can solve a problem accurately, quickly and with less effort.

Before choosing ML, an engineer should first understand the problem, define the desired outcome, check whether suitable data is available and decide how success will be measured.

The goal is to choose the simplest approach that meets the requirements.

## 2. Define the Problem Before Choosing a Technique

Consider this problem:

**Problem:** Identify chip designs that may fail timing.

**Desired outcome:** Help engineers identify designs that need further timing analysis before they are accepted.

Before choosing a solution, we should ask:

- What exactly are we trying to identify?
- Can a fixed rule solve the problem adequately?
- Do we have reliable historical measurements and timing results?
- What information will be available when a prediction is made?
- How will we measure success?
- What could happen if the prediction is incorrect?

Answering these questions helps us decide whether ML is necessary.

## 3. Solution A - Rule-Based Approach

A rule-based system follows conditions written by a programmer. It does not learn those rules from training data.

For example, an engineer could define a rule that flags a design when its measured delay exceeds a specified timing limit.

**Illustrative rule:**

```text
IF measured_delay > timing_limit
    Flag the design for review
ELSE
    Do not flag it using this rule
```

The timing limit must come from the relevant design requirements. The example does not define a universal timing limit.

### Advantages

- Simple to understand and implement.
- Does not require a training dataset.
- Produces predictable results when the inputs and rules are the same.
- Easy to verify when the rule is clearly defined.
- Suitable when the conditions are stable and the rules are known.

### Limitations

- A programmer must define the rules.
- Complex situations may require many rules.
- Fixed rules may not handle patterns that are difficult to express manually.
- If conditions change, the rules may need to be updated.

## 4. Solution B - Possible ML Approach

An ML system could learn from historical chip-design measurements and their known timing outcomes.

For example, a supervised classification model could use features such as design measurements and relevant timing information to predict whether a design is likely to pass or fail.

**Illustrative process:**

```text
Historical design measurements
          +
Verified timing outcomes
          |
          v
    Train an ML model
          |
          v
       New design
          |
          v
   Predicted timing status
          |
          v
 Engineer reviews the result
```

### Advantages

- Can learn patterns from historical examples.
- May identify relationships that are difficult to express using fixed rules.
- Can combine multiple relevant features to make predictions.
- Can be updated when sufficient new, reliable data becomes available.

### Limitations

- Requires suitable, reliable and representative training data.
- Predictions can be wrong.
- The model may perform poorly on designs that differ from its training data.
- Training, evaluation, deployment and monitoring require additional effort.
- A prediction may be difficult to explain fully, depending on the model.

An ML model should not replace the required timing-analysis and verification process. Its prediction can support engineers, but it should not automatically prove that a design passes timing.

## 5. Comparison: Rule-Based vs. ML

| Point | Rule-based solution | ML solution |
|---|---|---|
| How it works | Follows explicitly programmed conditions | Learns patterns from training data |
| Data requirements | Requires the inputs needed to apply its rules, but not a training dataset | Requires suitable training examples and appropriate inputs at prediction time |
| Best suited for | Clear, stable and well-defined rules | Problems where useful patterns can be learned from representative data |
| Adaptability | Rules must be changed manually when needed | Can be retrained using new data when justified |
| Complexity | Simple when there are few rules; can become difficult with many exceptions | Requires model development and supporting data systems |
| Failure modes | Incorrect thresholds, missing conditions or outdated rules | Poor data, incorrect labels, bias, overfitting, data changes or incorrect predictions |
| Evaluation | Test the rules against requirements and known cases | Evaluate on separate data using suitable metrics and compare against a baseline |
| Maintenance | Review and update rules when conditions change | Monitor performance, data quality and changes; update the model when needed |

## 6. How Should Success Be Measured?

Before building either solution, we should decide what a successful result means.

For the chip-timing example, useful evaluation questions include:

- How many designs that actually fail timing are identified?
- How many passing designs are unnecessarily flagged?
- Does the solution reduce engineering review effort?
- Does it help engineers identify risky designs earlier?
- Does it perform reliably on different types of designs?

For an ML classifier, recall for the Fail class can measure how many actual failing designs are identified. False positives can also be measured because unnecessarily flagging passing designs may increase engineering workload.

The rule-based and ML approaches should be evaluated on comparable cases using the same relevant success criteria.

A model with good prediction metrics is not automatically useful if it does not improve the engineering workflow.

## 7. What Happens If a Prediction Is Incorrect?

Incorrect predictions can have different consequences.

### False negative

A design that fails timing is predicted to pass.

**Possible consequence:** Engineers may overlook a design that needs further investigation.

### False positive

A design that passes timing is predicted to fail.

**Possible consequence:** Engineers may spend additional time reviewing a design that does not need that level of attention.

Both errors matter, but their costs may differ. The acceptable trade-off depends on the engineering requirements.

For this reason, the solution should be tested carefully, and important design decisions should continue to use the required verification procedures.

## 8. When Should We Choose ML?

ML may be worth considering when:

- The problem has a clear, measurable goal.
- Reliable and representative data is available.
- The data contains useful patterns for predicting the desired outcome.
- A simple rule-based approach does not perform adequately.
- The expected improvement justifies the cost and maintenance of ML.
- The consequences of incorrect predictions can be managed.

A rule-based solution may be preferable when:

- The requirements can be expressed as clear conditions.
- The rules are stable and cover the important cases.
- The existing solution already meets the required performance.
- Training data is unavailable or unsuitable.
- The additional complexity of ML is not justified.

The decision should be based on evidence rather than the assumption that ML is always better.

## Conclusion

A problem involving data does not automatically require Machine Learning.

For identifying chip designs that may fail timing, a rule-based solution may be sufficient when the requirements are clear and stable. An ML solution may be useful if reliable historical data contains patterns that help identify risky designs beyond what simple rules can achieve.

The engineer should define the problem first, compare both approaches, measure their performance and consider the consequences of incorrect results. The best solution is the one that meets the requirements reliably with an appropriate level of complexity and cost.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
