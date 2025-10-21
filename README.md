# 🧠 pycircuit-sim — Project Report

## 🏷️ Project Title
**pycircuit-sim** — A Lightweight Python-Based Circuit Simulator

## ⚡ Brief One Line Summary
A simple, educational DC circuit simulator built in Python for learning, experimentation, and rapid prototyping.

## 📘 Overview
`pycircuit-sim` is an open-source Python library that performs **DC circuit analysis** using **Modified Nodal Analysis (MNA)**.  
It’s designed to help students, educators, and hobbyists understand the mathematics and logic behind circuit simulation — without the complexity of industrial tools like SPICE.

## ❓ Problem Statement
Most circuit simulators (like SPICE or LTSpice) are powerful but **not beginner-friendly**.  
Their complexity makes it hard to grasp how the underlying equations are formed and solved.  
`pycircuit-sim` aims to **bridge that gap** by providing a **minimal, transparent, and readable** Python implementation of DC analysis.

## 🧩 Dataset
There is no external dataset.  
Instead, users define circuits via simple **netlist files** that describe components and connections.

Example netlist:
```text
* Simple voltage divider
V1 n2 0 5
R1 n1 n2 1000
R2 n1 0 2000
```

## 🧰 Tools and Technologies
| Category | Tools |
|-----------|--------|
| **Language** | Python 3.8+ |
| **Libraries** | NumPy |
| **Testing** | Pytest |
| **Packaging** | setuptools |
| **Version Control** | Git / GitHub |

## 🔬 Methods
The simulator implements **Modified Nodal Analysis (MNA)**, a standard approach in circuit theory.

### Algorithm Steps:
1. Build the **conductance matrix (G)** using resistor values.  
2. Add equations for **independent voltage sources**.  
3. Solve the resulting linear system `A·x = z` using NumPy’s solver.  
4. Output:
   - Node voltages (relative to ground)
   - Currents through voltage sources

## 💡 Key Insights
- Demonstrates how circuits can be solved using **linear algebra**.  
- Serves as a **learning tool** to understand nodal equations.  
- The architecture is modular — easy to extend for new component types (current sources, dependent sources, etc.).  
- Educational readability was prioritized over performance or complexity.

## 📊 Dashboard / Model / Output

### Example Code
```python
from pycircuit_sim.core import Circuit

c = Circuit()
c.add_resistor("R1", "n1", "0", 1000)
c.add_resistor("R2", "n1", "n2", 2000)
c.add_voltage_source("V1", "n2", "0", 5)

res = c.solve()
print(res)
```

### Example Output
```python
{
  'nodes': {'0': 0.0, 'n1': 3.3333, 'n2': 5.0},
  'vsrc_currents': {'V1': 0.001667}
}
```

## ⚙️ How to Run this Project

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/pycircuit-sim.git
cd pycircuit-sim
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
# or
pip install .
```

### 3. Run an example
```bash
python examples/run_example.py examples/voltage_divider.net
```

### 4. Run tests
```bash
pytest
```

## 📈 Results & Conclusion
- The simulator accurately computes **DC node voltages** and **source currents** for resistive circuits.  
- Verified with test cases (e.g., voltage divider).  
- Confirms that a **functional circuit solver** can be implemented concisely and clearly in Python.  

This project demonstrates the **core of circuit simulation theory** while remaining small enough for teaching and experimentation.

## 🚀 Future Work
- Add **current sources** and **controlled sources (VCCS, CCCS)**  
- Extend to **AC** and **transient (time-domain)** analysis  
- Develop a **GUI or web-based circuit builder**  
- Integrate **sparse solvers** for large circuits  
- Create an **educational visualization dashboard**

## 👤 Author & Contact
**Author:** BIHAR GOURAV  
**Email:** bihargaurav56@gmail.com  
**GitHub:** [github.com/BGourav05/pycircuit-sim-part2](https://github.com/BGourav05/pycircuit-sim-part2)
