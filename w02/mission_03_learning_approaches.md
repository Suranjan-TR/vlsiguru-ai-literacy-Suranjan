# Mission 3 - Understand the Main ML Approaches

## 1. Introduction

Machine Learning (ML) systems can learn in different ways depending on the type of information or feedback available.

The three main approaches are:

- **Supervised learning:** learns from examples with known answers.
- **Unsupervised learning:** finds patterns in data without known answers.
- **Reinforcement learning:** learns through actions and rewards or penalties.

Self-supervised learning is a related approach in which the system creates its own learning targets from the data.

## 2. Comparison of Learning Approaches

| Learning approach | Training signal | What it produces | One limitation | Example |
|---|---|---|---|---|
| Supervised learning | Labelled examples containing inputs and correct answers | A model that predicts labels or numerical values | Requires labelled training data, which can take time to prepare | Predicting whether a chip design passes timing |
| Unsupervised learning | Unlabelled data without predefined correct answers | Patterns, groups or relationships in data | Discovered groups may be difficult to interpret | Grouping similar chip-design runs |
| Reinforcement learning | Rewards or penalties received after taking actions | A policy or strategy for choosing actions | Designing useful rewards and learning efficiently can be difficult | Training a robot to move safely |
| Self-supervised learning | Targets generated from the input data itself | A model that learns useful patterns or representations from data | The generated learning task may not capture everything needed for the final task | Hiding a word in a sentence and predicting it |

## 3. How Each Learning Approach Works

### A. Supervised Learning

Supervised learning uses labelled data. Each training example contains input features and a known correct answer.

The model makes predictions, compares them with the correct answers and adjusts to reduce its errors.

**Simple diagram:**

```text
Labelled data
(Input + Correct answer)
          |
          v
      ML Model
          |
          v
     Prediction
          |
          v
Compare with correct answer
          |
          v
     Reduce error
          |
          v
   Trained model
```

**Example:** A model receives historical chip-design measurements with known timing status. It learns patterns that help predict whether a new design will pass or fail timing.

**When suitable:** When labelled examples are available and the goal is to predict a known outcome.

### B. Unsupervised Learning

Unsupervised learning uses data without predefined correct answers. The model tries to discover patterns, similarities or groups within the data.

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

**Example:** A model groups chip-design runs with similar power, performance and area measurements without being told which groups should exist.

**When suitable:** When the data has no labels and the goal is to explore its structure or discover patterns.

**Limitation:** The discovered groups do not automatically have meaningful names or prove that the grouping is useful.

### C. Reinforcement Learning

Reinforcement learning involves an agent interacting with an environment. The agent takes an action and receives feedback in the form of a reward or penalty.

Over time, it learns a strategy for choosing actions that aim to maximise the total reward.

**Simple diagram:**

```text
       +------------------+
       |    Environment   |
       +------------------+
          |            ^
   State and reward    | Action
          |            |
          v            |
       +------------------+
       |      Agent       |
       +------------------+
                |
                v
       Learns a strategy
```

**Example:** A robot tries different movements. Successful movements receive rewards, while unsuccessful movements may receive penalties. It learns a better strategy through repeated interaction.

**When suitable:** When a problem involves a sequence of actions and feedback about how well those actions perform.

**Limitation:** Learning may require many interactions, and a poorly designed reward can encourage unwanted behaviour.

### D. Self-Supervised Learning

Self-supervised learning creates training targets from the data itself instead of depending on manually supplied labels.

For example, a system receives this sentence:

"The chip passed the timing test."

It hides the word "timing" and tries to predict the missing word using the remaining sentence.

**Simple diagram:**

```text
Original data
      |
      v
Create a learning task
(e.g. hide part of the input)
      |
      v
Model predicts missing part
      |
      v
Compare prediction with
the original data
      |
      v
Learn from the prediction error
```

**When suitable:** When large amounts of unlabelled data are available and useful training targets can be created from the data itself.

**Limitation:** Predicting hidden parts of the data does not guarantee that the model will perform every desired task well.

## 4. Self-Supervised Learning vs. Unsupervised Learning

Both approaches can use data without human-provided labels, but their learning processes differ.

| Point | Unsupervised learning | Self-supervised learning |
|---|---|---|
| Human-provided labels | Not required | Not required for the self-supervised training task |
| How it learns | Finds patterns, similarities or groups in data | Creates targets from the data and learns to predict them |
| Example | Grouping similar chip-design runs | Predicting a hidden word in a sentence |
| Main purpose in these examples | Discover the structure of data | Learn from a prediction task created using the data |

Self-supervised learning is sometimes discussed as a type of unsupervised learning because it does not require manually labelled examples. However, it is useful to distinguish it as a separate approach when comparing learning signals.

The key difference is that self-supervised learning creates an explicit prediction target from the input data. Conventional unsupervised learning can instead focus on discovering structure, such as groups, without using that kind of target.

Therefore, self-supervised learning is related to unsupervised learning, but the two terms do not describe exactly the same learning process in every context.

## 5. Which Approach Should Be Used?

The appropriate approach depends on the available data and the goal.

- **Use supervised learning** when historical examples contain known answers and the goal is to predict an outcome.
- **Use unsupervised learning** when answers are unavailable and the goal is to find groups or patterns.
- **Use reinforcement learning** when an agent must choose actions and learn from rewards or penalties.
- **Use self-supervised learning** when targets can be generated from unlabelled data to help a model learn useful patterns.

For example, predicting whether a chip design passes timing can use supervised learning if historical timing labels are available. Grouping similar design runs can use unsupervised learning. Learning to optimise a sequence of design choices through reward feedback could be framed as reinforcement learning, while learning from unlabelled technical text by predicting hidden words is an example of self-supervised learning.

## Conclusion

The main difference between learning approaches is the training signal they use. Supervised learning uses known answers, unsupervised learning discovers patterns without predefined answers, and reinforcement learning uses feedback from actions. Self-supervised learning creates its own targets from the data.

Understanding these differences helps in selecting an appropriate approach for a problem.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
