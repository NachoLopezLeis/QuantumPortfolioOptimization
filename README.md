# IbexQuantumVQE: Quantum Portfolio Optimization for IBEX 35

This project implements a quantum portfolio optimization algorithm using the Variational Quantum Eigensolver (VQE) method on real IBEX 35 stock data. The code downloads historical prices of the 29 IBEX 35 companies, formulates the optimal portfolio selection problem as a QUBO, converts it into a Hamiltonian, and solves it using Qiskit on a quantum simulator.

---

## Features

- **Automatic data download** from Yahoo Finance for IBEX 35 components.
- **QUBO formulation** of the portfolio problem: maximize expected return and minimize risk with a budget constraint.
- **Hamiltonian conversion** for quantum simulation.
- **Manual VQE implementation** using Qiskit and `scipy.optimize`.
- **GPU-accelerated simulation** with AerSimulator.
- **Selection and analysis** of the best quantum portfolios found.

---

## Requirements

- Python 3.11+
- Compatible GPU (optional, recommended for faster simulation)
- Python libraries:
    pip install numpy pandas yfinance matplotlib scipy
    qiskit==2.0.0 qiskit-aer==0.17.0
    qiskit-ibm-runtime==0.38.0 qiskit_algorithms==0.3.1
    'qiskit[visualization]'

---

## Usage

1. **Clone this repository and open the notebook** in Jupyter or Google Colab.
2. **Run the cells sequentially.** The main workflow is in the `main()` function.

### Run as a script

If running as a standalone script:   if name == "main": main()


---

## Code Structure

- **Data download and preprocessing:**  
  `get_ibex35_data()` downloads adjusted closing prices, cleans data, computes returns, mean returns, and annualized covariance matrix.

- **Problem formulation:**  
  `build_portfolio_problem()` creates the QUBO and converts it into a Pauli operator Hamiltonian.

- **Manual VQE:**  
  `ManualVQE` class implements the variational optimization loop with a real amplitude ansatz and quantum expectation estimation.

- **Evaluation and analysis:**  
  Simulates measurements, identifies the most probable portfolios, and calculates their return, risk, and return/risk ratio.

---

## Customizable Parameters

- **budget:** Number of stocks to select (default 5).
- **risk_factor:** Weight of risk in the objective function (default 0.5).
- **maxiter:** Maximum classical optimizer iterations (default 100).

Modify these parameters in the call to `build_portfolio_problem()` or when instantiating `ManualVQE`.

---

## Expected Output

The program prints:

- Number of VQE parameters.
- Optimization progress.
- Top 3 most probable quantum portfolios with:
  - Selected stocks.
  - Expected return.
  - Total risk.
  - Return/risk ratio.

---

## Technical Notes

- The Hamiltonian is ensured to be real and positive definite.
- The simulator uses the `statevector` method and can leverage GPU acceleration.
- The code handles missing or inconsistent Yahoo Finance data robustly.

---



**Explore the frontier of finance and quantum computing with IbexQuantumVQE!**
