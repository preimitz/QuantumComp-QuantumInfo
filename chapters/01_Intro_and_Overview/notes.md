# 📘 Chapter 1: Introduction and Quantum Bits

## 🔑 Key Concepts

- **Qubits**: Basic unit of quantum information.
  - State: |ψ⟩ = α|0⟩ + β|1⟩
  - Constraint: |α|² + |β|² = 1

- **Bloch Sphere Representation**:
  - Visual representation of a qubit state:
    - |ψ⟩ = cos(θ/2)|0⟩ + e^{iφ} sin(θ/2)|1⟩
  - Useful for understanding single-qubit gate effects.

- **Measurement**:
  - In the computational basis: collapse to |0⟩ or |1⟩.
  - Probabilities: |α|² for |0⟩, |β|² for |1⟩.
  - Irreversible process – destroys superposition.

---

## 🔄 Quantum vs Classical Bits

| Classical Bit | Quantum Bit (Qubit)         |
|---------------|------------------------------|
| 0 or 1        | Superposition of 0 and 1      |
| Deterministic | Probabilistic outcomes        |
| Copiable      | **No-Cloning Theorem** applies |

---

## 📐 Dirac Notation (Bra-Ket)

- **Kets**:
  - |0⟩ = [1, 0]ᵗ
  - |1⟩ = [0, 1]ᵗ

- **Bras**:
  - ⟨0| = [1, 0]
  - ⟨1| = [0, 1]

- **Inner product**: ⟨ψ|ϕ⟩
- **Outer product**: |ψ⟩⟨ϕ|

---

## ⚙️ Quantum Gates (Single Qubit)

| Gate | Matrix                                       | Effect              |
|------|----------------------------------------------|---------------------|
| X    | [[0, 1], [1, 0]]                             | Bit-flip (NOT)      |
| H    | (1/√2) * [[1, 1], [1, -1]]                   | Creates superposition |
| Z    | [[1, 0], [0, -1]]                            | Phase-flip          |

---

## 🧪 Experiment Idea (Jupyter Notebook)

Apply a Hadamard gate to |0⟩ and observe measurement outcomes.

```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator
from qiskit.visualization import plot_histogram

qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)

sim = AerSimulator()
qc = qc.transpile(sim)
result = sim.run(qc, shots=1000).result()
counts = result.get_counts()

plot_histogram(counts)

