# Mission 9 - Machine Learning in Semiconductor Design Verification

## Case Study: Using ML to Improve Functional Coverage Closure

## 1. Introduction

Design Verification (DV) is an important stage in semiconductor development. Its purpose is to check whether a hardware design behaves according to its specification.

Verification engineers use simulation, testbenches, assertions and functional coverage to check different behaviours of a design. In constrained-random verification, the testbench generates different input combinations and checks the design's responses.

However, some tests may repeatedly exercise functionality that has already been covered. Reaching important coverage goals can therefore require many simulation runs and significant engineering effort.

Machine Learning (ML) could help by identifying or selecting tests that are more likely to exercise new functionality. This case study explores how ML could support functional coverage closure without replacing conventional verification.

## 2. Engineering Problem

The main problem is that random or constrained-random testing may take a long time to reach certain functional coverage goals.

For example, when verifying a FIFO, engineers may need to test:

- Writing data into the FIFO.
- Reading data from the FIFO.
- Simultaneous read and write operations.
- FIFO full and empty conditions.
- Boundary cases and different operating conditions.

Some combinations may occur frequently, while others are difficult to reach. Engineers may need to adjust constraints or create additional sequences to cover the remaining scenarios.

**Goal:** Reduce unnecessary simulation effort while continuing to explore important functionality and meet the required verification goals.

## 3. Data Needed

An ML system could use information collected from previous simulation runs.

Possible input data includes:

- Test or sequence configuration.
- Randomised input values and relevant constraints.
- Functional coverage before and after a simulation.
- Coverage bins hit by each test.
- Simulation results and runtime.
- Relevant design configuration and operating conditions.

The data should be collected consistently, and coverage results should be checked for correctness.

For example, if a test exercises a previously uncovered FIFO condition, the system could learn which test configurations are associated with new coverage.

## 4. Possible ML Approach

One possible approach is **supervised classification**.

The model would learn from historical test data labelled according to whether each test produced additional functional coverage.

The expected output could be:

- **Likely to add coverage**
- **Unlikely to add coverage**

The verification environment could use this prediction to prioritise promising tests for simulation.

### Simplified workflow

```text
Previous simulation data
(Test configurations + coverage results)
                 |
                 v
        Prepare labelled data
                 |
                 v
          Train ML model
                 |
                 v
    Predict whether a new test
      may add functional coverage
                 |
                 v
      Prioritise selected tests
                 |
                 v
       Run actual simulations
                 |
                 v
     Check coverage and correctness
                 |
                 v
       Update the verification plan
```

The ML model predicts which tests may be useful. The simulator still needs to execute the tests, and the coverage results must be checked to confirm what was actually achieved.

## 5. Evaluation and Success Measures

The ML-assisted approach should be compared with a conventional random or constrained-random verification baseline.

Useful measures include:

- **Functional coverage:** How much of the intended functionality has been exercised?
- **Simulation cycles or runtime:** How much simulation effort is required?
- **Coverage improvement:** How quickly does the approach reach important coverage goals?
- **Bug detection:** Does the approach continue to detect design errors?
- **Reproducibility:** Can important results be repeated and investigated?

A successful approach should improve verification efficiency without reducing the quality of verification.

High functional coverage alone does not prove that the design is bug-free. Engineers must also consider assertions, test results, design requirements and other appropriate verification methods.

## 6. Research Evidence

Two research sources demonstrate that ML-based approaches to verification coverage are being investigated.

### Source 1: NVIDIA Research

NVIDIA Research published work on selecting RTL tests using unsupervised learning from fast functional simulation. The researchers studied ML-based test selection for two units from a production GPU design and reported that their approach could reduce RTL simulation runtime by up to 85% compared with a constrained-random test-selection baseline while achieving the same RTL functional coverage.

This is a research demonstration. The reported result applies to the studied designs and experimental setup; it should not be assumed to apply to every verification project.

Source: https://research.nvidia.com/publication/2023-07_late-breaking-results-test-selection-rtl-coverage-unsupervised-learning-fast

### Source 2: IEEE Conference Publication

The paper *Accelerated Design Verification Coverage Closure Using Machine Learning*, published in the 2025 VLSI Design conference proceedings, describes an ML approach that predicts whether a randomly generated stimulus is likely to provide additional coverage. The proposed flow uses the prediction to guide which stimuli are simulated.

This research directly addresses the problem of spending simulation time on tests that do not add new coverage.

Source: https://doi.org/10.1109/VLSID64188.2025.00070

These sources describe research approaches and results. They do not establish that every commercial DV team has deployed these exact methods in production.

## 7. Limitations and Engineering Risks

ML can support verification, but it also introduces limitations.

- **Incomplete training data:** The model may not learn from rare scenarios if they are missing from historical simulations.
- **Prediction errors:** A test predicted to add little coverage may still discover an important corner case or design bug.
- **Changing designs:** A model trained on one design or configuration may perform poorly on another.
- **Coverage is not correctness:** High coverage does not prove that every behaviour is correct or that every bug has been found.
- **Additional complexity:** Preparing data, training models and integrating them into the simulation flow requires effort.
- **Human oversight:** Verification engineers must review results, investigate coverage gaps and ensure that important tests are not skipped solely because of an ML prediction.

For these reasons, ML should guide test prioritisation rather than replace required verification checks.

## Conclusion

Machine Learning can support Design Verification by helping engineers prioritise tests that are more likely to improve functional coverage. This may reduce wasted simulation effort and help verification teams reach coverage goals more efficiently.

Research from NVIDIA and an IEEE conference publication demonstrates that ML-based test selection and coverage prediction are active research areas. However, the usefulness of an approach depends on the design, available data and evaluation method.

ML should therefore be treated as an assistant to the verification process. Simulation, coverage analysis, assertions and engineering judgement remain essential for establishing confidence in a hardware design.

## Sources

See [`sources.md`](sources.md) for the full source list and the claims supported by each source.
