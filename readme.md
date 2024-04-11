# YQuantum Hackathon - State preparation for quantum computing Monte Carlo
By The Hartford and Capgemini

## Introduction

Quantum computing, with its extraordinary promise of computational speedups, stands poised to revolutionize various industries. Among these, the insurance sector is particularly ripe for transformation. Enter the technique known as **Quantum Computing Monte Carlo** (QCMC), a quantum counterpart to the classical “Monte Carlo” method. By harnessing the unique properties of quantum systems, QCMC holds the potential to drive significant improvements in insurance processes.

## Monte Carlo for insurance

Before we investigate QCMC, let’s look at Monte Carlo simulations on classical computers. Monte Carlo methods involve **random sampling** and **deterministic computation**. Here’s a concise breakdown:

1. **Random Sampling**: We generate random inputs (often following specific probability distributions) for a system’s parameters. These inputs represent different scenarios.
2. **Deterministic Computation**: For each set of sampled inputs, we perform a deterministic computation. The result provides an estimate for the desired quantity.

The big challenge is the fact that to get a good aggregation, we need many iterations. Specifically, to achieve an aggregation with an error , we need ) iterations.

### Applications in insurance

**Monte Carlo methods** find a special place in the insurance industry. Here are some applications of Monte Carlo methods in the insurance industry:

- **Risk Assessment:** Simulating scenarios helps insurers understand potential outcomes.
- **Premium Calculations:** Monte Carlo aids in estimating insurance premiums.
- **Reserve Estimation:** Insurers use it to estimate reserves for future claims.
- **Stress Testing:** Assessing financial stability through extreme scenarios.

During this hackathon, you will focus on reserve estimation.

### Conditional Value-at-Risk

Conditional Value-at-Risk (CVaR), also known as Expected Shortfall (ES), is a risk measure that quantifies the expected loss of an investment portfolio over a specific time under extreme market conditions. Unlike Value-at-Risk (VaR) which only considers the maximum loss at a certain confidence level, CVaR considers the severity of the losses beyond the VaR threshold. This makes CVaR a more comprehensive measure of risk as it provides an estimate of the expected value of the extreme losses. In the context of insurance, CVaR can be used to assess the potential losses an insurer could face in extreme scenarios, thereby aiding in reserve estimation and stress testing. It’s particularly useful in the context of tail risk management, where the focus is on extreme events that have a small probability of occurrence but could lead to significant losses.

## Quantum Computing Monte Carlo

Monte Carlo methods are ubiquitous in insurance. Sometimes, however, it is not possible to run the Monte Carlo simulations as you would like, because they take too much computer power. Quantum Computing Monte Carlo promises a quadratic speed-up, as it is based on Grover’s algorithm. The result is that the accuracy no longer scales as , rather the QCMC scales as .

The result is algorithmic speed-up, which translates to:

- Faster results with the same accuracy
- Higher accuracy in the same calculation time
- More complex models (fewer assumptions) with the same accuracy in the same calculation time

### Amplitude Estimation

QCMC is based on Amplitude Estimation<sup>[\[1\]](#footnote-1)</sup>. In Amplitude Estimation, you use phase estimation and amplitude amplification to estimate the amplitude of a marked state. The trick is to encode a value of interest in the amplitude of the marked state. Previous work has done this for risk analysis<sup>[\[2\]](#footnote-2)</sup> and option pricing<sup>[\[3\]](#footnote-3)</sup>.

For more information about how to practically run a CVaR calculation, please refer to the excellent tutorial by IBM attached.

### State Preparation

The question now is how to load the value of interest in the amplitude. There exist methods for this<sup>[\[4\]](#footnote-4)</sup>, however, loading the state has such high overhead in terms of circuit depth, that this sub procedure might negate any computational advantage that QCMC has to offer<sup>[\[5\]](#footnote-5)</sup>.

## The challenge

Your challenge is to create a toy example Quantum Computing Monte Carlo pipeline (e.g., using Qiskit/TKET) to estimate risk and subsequently estimate how much reserves the insurer should keep.

In that pipeline, focus on the state preparation method and try to come up with a method that fits the NISQ constraints, i.e., relatively many qubits, with relatively poor quality. I.e., use ancilla qubits to decrease the circuit depth. (hint: which gates can a quantum computer execute?)

Now, can you estimate how your pipeline scales? In terms of circuit depth, circuit width, and accuracy.

## Setup

1. Clone this repository:
    ```
    git clone https://github.com/your_username/yquantum-hartford-capgemini.git
    # TODO put in URL
    ```

2. Navigate to the cloned repository:
    ```
    cd yquantum-hartford-capgemini
    ```

3. Create a new conda environment from the `environment.yml` file:
    ```
    conda env create -f environment.yml -n yquantum
    ```

4. Activate the new environment:
    ```
    conda activate yquantum
    ```

Now, you're ready to run the project!

In `notebooks/problem-setting.ipynb`, the problem is expressed in code.

## References

1. Brassard, G., Høyer, P., Mosca, M. & Tapp, A. _Quantum Amplitude Amplification and Estimation_. (2000). [↑](#footnote-ref-1)

2. Woerner, S. & Egger, D. J. Quantum risk analysis. _npj Quantum Information_ **5**, (2019). [↑](#footnote-ref-2)

3. Stamatopoulos, N. _et al._ Option Pricing using Quantum Computers. (2019) doi:[10.22331/q-2020-07-06-291](https://doi.org/10.22331/q-2020-07-06-291). [↑](#footnote-ref-3)

4. Grover, L. & Rudolph, T. Creating superpositions that correspond to efficiently integrable probability distributions. Preprint at <http://arxiv.org/abs/quant-ph/0208112> (2002). [↑](#footnote-ref-4)

5. Herbert, S. The Problem with Grover-Rudolph State Preparation for Quantum Monte-Carlo. _Phys. Rev. E_ **103**, 063302 (2021). [↑](#footnote-ref-5)

6. Akhalwaya, I. Y. _et al._ A Modular Engine for Quantum Monte Carlo Integration. Preprint at http://arxiv.org/abs/2308.06081 (2023).