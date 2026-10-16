# Mission 5 - Understand the Anatomy of an ML Model

## 1. Introduction

A Machine Learning (ML) system learns patterns from examples during training. After training, the resulting model can use those learned patterns to make predictions on new inputs.

To understand this process, we need to know what an algorithm, a model, parameters, training, inference, loss and optimisation mean.

## 2. Algorithm vs. Model vs. Learned Parameters

These three terms are related, but they have different meanings.

| Term | Meaning | Example |
|---|---|---|
| Algorithm | The method or procedure used to learn from training data | Linear regression training procedure |
| Model | The learned system that uses patterns from data to make predictions | A trained model that estimates chip delay |
| Learned parameters | Values learned from training data that determine the model's behaviour | The slope and intercept of a linear regression model |

**Simple explanation:**

- An algorithm is the method used for learning.
- A model is the result after learning.
- Parameters are learned values that help the model produce predictions.

For example, a linear regression algorithm can learn parameters from historical chip-design measurements. The trained model then uses those parameters to estimate the delay of a new design.

Different ML methods learn different kinds of parameters or internal representations.

## 3. Training vs. Inference

### A. Training

Training is the process of learning from examples.

The system uses training data to learn patterns. In supervised learning, each example contains input features and a known target answer.

The model makes predictions during training, compares them with the target answers, calculates a loss and adjusts its parameters to improve its predictions.

### B. Inference

Inference is the process of using a trained model to make predictions on new input data.

During ordinary inference, the model uses its already learned parameters. It does not normally update them just because it receives a new input.

**Example:**

Suppose a model is trained using historical chip-design measurements and their known delays.

- During training, it learns a relationship between design measurements and delay.
- During inference, it receives measurements from a new design and estimates its delay.

## 4. Labelled Flow Diagram: From Examples to Prediction

The following diagram shows the main stages of supervised learning.

```text
       Training examples
    (Inputs + Target answers)
               |
               v
       Choose an algorithm
               |
               v
        Initial model
               |
               v
     Make training predictions
               |
               v
    Compare predictions with
        target answers
               |
               v
        Calculate loss
     (Measure prediction error)
               |
               v
         Optimisation
     (Adjust learned parameters)
               |
               +------------------+
               |                  |
               +--> Repeat until  |
                    suitable       |
                    training       |
                    stopping point |
               |                  |
               v                  |
          Trained model <----------+
               |
               v
      New input data
               |
               v
          Inference
               |
               v
       Prediction result
```

The diagram is a simplified view of supervised model training. Actual training procedures differ across ML methods, and not every method uses target answers, loss calculations or optimisation in exactly this way.

## 5. What Are Loss and Optimisation?

### A. Loss

Loss is a numerical measure of how far a model's prediction is from the desired answer, according to a chosen loss function.

For example, suppose the actual chip delay is 8 ns.

- Predicted delay: 8.2 ns
- Actual delay: 8 ns
- Prediction error in absolute terms: 0.2 ns

If the predicted delay were 10 ns, the absolute error would be 2 ns.

The second prediction has a larger absolute error. A suitable loss function can measure this difference.

Loss functions do not all measure error in the same way. For example, some use squared errors, while others are designed for classification.

### B. Optimisation

Optimisation is the process used to adjust a model's learnable parameters to improve its objective, often by reducing the loss during training.

For example, a linear regression model may initially make inaccurate delay predictions. Its training procedure adjusts its learned parameters so that its predictions better match the training examples.

**Remember:**

- Loss measures how well or poorly the model predicts according to a chosen measure.
- Optimisation changes learnable parameters to improve the training objective.
- Training repeats the learning process according to the selected method and stopping criteria.

A low training loss does not automatically guarantee good predictions on new data. The model must also generalise to examples it has not seen during training.

## 6. Understanding Linear Regression

Linear regression is a supervised learning method used to predict a numerical value.

It learns a relationship between input features and a numerical target using example data.

For a simple example, suppose we want to predict chip delay using clock frequency. We have historical examples containing the frequency and measured delay.

The model learns a relationship that can be represented conceptually as:

\[
\text{Predicted delay} = w \times \text{Frequency} + b
\]

Here:

- **Frequency** is the input feature.
- **Predicted delay** is the model's output.
- **\(w\)** is the learned weight or slope.
- **\(b\)** is the learned bias or intercept.

The training procedure learns suitable values for \(w\) and \(b\) from the available examples.

### Simple example

Consider this illustrative dataset:

| Clock frequency (MHz) | Measured delay (ns) |
|---:|---:|
| 100 | 7.0 |
| 120 | 7.5 |
| 140 | 8.0 |
| 160 | 8.5 |

The algorithm uses these examples to learn a relationship between frequency and delay.

After training, the model can receive a new frequency, such as 150 MHz, and estimate the corresponding delay.

The estimate depends on the learned parameters. This example is illustrative only; real chip delay depends on many factors, not just clock frequency.

### Linear regression process

```text
Historical examples
(Frequency + Measured delay)
             |
             v
      Linear regression
          algorithm
             |
             v
    Learn slope and intercept
             |
             v
       Trained model
             |
             v
     New frequency input
             |
             v
     Predicted chip delay
```

Linear regression is useful when a numerical outcome can be estimated from a learned relationship between input features and the target. A simple linear model may not adequately represent complex relationships.

## 7. Important Points to Remember

- An algorithm is a method for learning; a model is the learned system.
- Learned parameters determine how a model behaves.
- Training is the learning process; inference uses the trained model to make predictions.
- In supervised learning, predictions can be compared with known target answers.
- Loss measures prediction error according to a chosen function.
- Optimisation adjusts learnable parameters to improve the training objective.
- Linear regression learns a relationship from example inputs and numerical outcomes.
- Different ML methods learn in different ways.
- Good performance on training examples does not guarantee good performance on unseen examples.

## Conclusion

An ML model is created by applying a learning method to data. During supervised training, the system can compare predictions with known answers and use loss and optimisation to improve its learned parameters. Once trained, the model uses those parameters during inference to predict outcomes for new inputs.

Linear regression provides a simple example of this process because it learns a relationship between input features and a numerical target.

## Sources

See [`sources.md`](sources.md) for the sources used in this mission.
