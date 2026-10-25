
# Mission 3 - Understand the Main ML Approaches

## 1. Introduction

Machine Learning (ML) systems can learn in different ways depending on the type of data available and the feedback provided during training.

The five commonly discussed ML approaches are:

- **Supervised learning:** Learns from labelled examples containing inputs and correct answers.
- **Unsupervised learning:** Finds patterns or groups in data without predefined labels.
- **Semi-supervised learning:** Learns using a small amount of labelled data and a larger amount of unlabelled data.
- **Self-supervised learning:** Creates its own training targets from the input data.
- **Reinforcement learning:** Learns a strategy through actions, rewards and penalties.

Each approach is useful for different types of problems. The choice depends on the available data, the learning objective and the feedback required.

## 2. Comparison of the Five Learning Approaches

| Learning approach | Training signal | What it produces | One limitation | Example |
|---|---|---|---|---|
| Supervised learning | Labelled examples containing inputs and correct answers | A model that predicts labels or numerical values | Requires labelled training data | Predicting whether a chip design passes timing |
| Unsupervised learning | Unlabelled data without predefined correct answers | Groups, patterns or relationships in data | Discovered patterns may be difficult to interpret | Grouping similar RTL simulation runs |
| Semi-supervised learning | A small labelled dataset combined with a larger unlabelled dataset | A model that learns from both labelled and unlabelled examples | Incorrect assumptions about unlabelled data can affect learning | Learning from a few labelled simulation failures and many unlabelled logs |
| Self-supervised learning | Targets generated from the input data itself | A model that learns useful patterns or representations | The generated task may not capture everything needed for the final task | Predicting a hidden word in a technical sentence |
| Reinforcement learning | Rewards or penalties received after taking actions | A policy or strategy for choosing actions | Learning can require many interactions, and reward design can be difficult | Learning a sequence of design-tuning actions to improve a performance measure |

## 3. How Each Learning Approach Works

### A. Supervised Learning

Supervised learning uses labelled data. Each training example contains input features and a known correct answer, called a label or target.

The model makes predictions, compares them with the correct answers and adjusts its parameters to reduce prediction errors during training.

**Simple diagram:**

```text
Labelled data
(Inputs + Correct answers)
         |
         v
     ML Model
         |
         v
     Prediction
         |
         v
Compare prediction
with correct answer
         |
         v
   Calculate error
         |
         v
Adjust model
during training
         |
         v
  Trained model
```

**Example:** A model receives historical chip-design measurements with known timing status. It learns patterns that help predict whether a new design is likely to pass or fail timing.

**When suitable:** When labelled examples are available and the goal is to predict a known outcome.

**Limitation:** Preparing accurate labels can require time and engineering effort.

### B. Unsupervised Learning

Unsupervised learning uses data without predefined correct answers. The model attempts to discover patterns, similarities, groups or relationships within the data.

**Simple diagram:**

```text
Unlabelled data
         |
         v
     ML Model
         |
         v
Find patterns and similarities
         |
         v
Groups or discovered patterns
```

**Example:** A model groups RTL simulation runs based on similar results, error counts or coverage measurements without being told in advance which groups should exist.

**When suitable:** When labelled answers are unavailable and the goal is to explore the structure of the data.

**Limitation:** The discovered groups may not have meaningful interpretations or be useful for the engineering task.

### C. Semi-Supervised Learning

Semi-supervised learning combines a small amount of labelled data with a larger amount of unlabelled data.

The labelled examples provide known answers, while the unlabelled examples can provide additional information about the data distribution. The exact training method depends on the algorithm.

**Simple diagram:**

```text
Small labelled dataset
          +
Large unlabelled dataset
          |
          v
   Semi-supervised
     ML training
          |
          v
      Trained model
          |
          v
Predictions for new data
```

**Example:** Suppose a verification team has a few simulation logs labelled as passing or failing, but many additional logs have not been classified. A semi-supervised approach could use both sets to help learn patterns associated with the results.

**When suitable:** When some reliable labelled examples are available but labelling the entire dataset is expensive or time-consuming.

**Limitation:** Incorrect labels or unsuitable assumptions about the unlabelled data can reduce model performance.

### D. Self-Supervised Learning

Self-supervised learning creates training targets from the data itself instead of depending on manually supplied labels for the training task.

The model makes predictions about part of the input and compares them with the original data to calculate a training error.

**Example:**

Original sentence:

"The chip passed the timing test."

The model receives a sentence with a missing word:

"The chip passed the _____ test."

It learns to predict the missing word, such as "timing".

**Simple diagram:**

```text
Original data
      |
      v
Create a learning task
(e.g., hide part of the input)
      |
      v
Model predicts missing part
      |
      v
Compare prediction with
the original data
      |
      v
Learn from prediction error
```

**Example in engineering:** A model could learn patterns from large collections of unlabelled technical documents by predicting masked words or missing parts of text.

**When suitable:** When large amounts of unlabelled data are available and useful training targets can be generated from that data.

**Limitation:** Success on the self-supervised task does not guarantee good performance on every downstream task.

### E. Reinforcement Learning

Reinforcement learning involves an agent interacting with an environment. The agent takes an action, receives feedback in the form of a reward or penalty, and learns a strategy for choosing actions.

The objective is generally to maximise the total expected reward over time.

**Simple diagram:**

```text
      +------------------+
      |   Environment    |
      +------------------+
          |          ^
          |          |
   State and reward  | Action
          |          |
          v          |
      +------------------+
      |      Agent       |
      +------------------+
               |
               v
      Learns a strategy
```

**Example:** A system could investigate a sequence of design-tuning actions, receiving rewards for improvements in a defined performance measure and penalties for undesirable outcomes. This is a possible application, not a claim that reinforcement learning is required for ordinary verification.

**When suitable:** When a problem involves a sequence of decisions and feedback about how well the actions perform.

**Limitation:** Learning may require many interactions, and a poorly designed reward function can encourage unwanted behaviour.

## 4. Semi-Supervised Learning vs. Self-Supervised Learning

Both approaches can make use of data that does not have manually supplied labels for every example. However, their training processes are different.

| Point | Semi-supervised learning | Self-supervised learning |
|---|---|---|
| Data used | A combination of labelled and unlabelled data | Targets are generated from the input data itself |
| Source of training signal | Human-provided labels for some examples, together with information from unlabelled data | A prediction target created from the data |
| Example | Learning from a few labelled simulation failures and many unlabelled logs | Predicting a hidden word in a technical sentence |
| Main idea | Make use of both labelled and unlabelled examples | Create a learning task from the data itself |

**Key difference:** Semi-supervised learning uses some manually labelled examples alongside unlabelled data. Self-supervised learning generates targets from the input data for its training task.

Self-supervised learning is sometimes considered a form of unsupervised learning in a broad classification because it does not require manually labelled targets for its pretraining task. It is often discussed separately because its explicit prediction task differs from approaches such as clustering.

## 5. How to Choose an ML Approach

The appropriate approach depends on the problem and the available data.

- **Supervised learning:** Choose it when reliable labelled examples are available and the goal is to predict an outcome.
- **Unsupervised learning:** Choose it when the goal is to discover patterns or groups without predefined labels.
- **Semi-supervised learning:** Consider it when a small labelled dataset is available alongside a much larger unlabelled dataset.
- **Self-supervised learning:** Consider it when a learning target can be generated from unlabelled data itself.
- **Reinforcement learning:** Consider it when an agent must make sequential decisions and learn from reward feedback.

### Connection to Design Verification (DV)

ML approaches could support different engineering tasks, depending on the data, model and validation requirements.

| DV-related task | Possible ML approach | Reason |
|---|---|---|
| Predicting pass/fail timing status from historical labelled results | Supervised learning | Known outcomes are available for training |
| Grouping similar simulation failures | Unsupervised learning | Groups can be explored without predefined labels |
| Learning from a few labelled failures and many unlabelled simulation logs | Semi-supervised learning | Both labelled and unlabelled examples are available |
| Learning representations from unlabelled RTL-related documentation or technical text | Self-supervised learning | Training targets can be generated from the text |
| Exploring sequences of tuning actions to optimise a defined objective | Reinforcement learning | Actions can be evaluated using reward feedback |

These are illustrative possibilities, not guarantees that ML will improve a DV workflow. Any model used in engineering must be evaluated on suitable data, and its results must not replace required simulation, coverage analysis or sign-off checks.

## Conclusion

The five commonly discussed ML approaches differ mainly in the training signal they use.

Supervised learning learns from labelled examples. Unsupervised learning discovers patterns without predefined labels. Semi-supervised learning combines labelled and unlabelled data. Self-supervised learning generates training targets from the data itself. Reinforcement learning learns strategies through actions and rewards.

Understanding these differences helps engineers select an approach that fits the problem, the available data and the intended outcome.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
