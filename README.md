# TLM Simulation of Graphene Sheet in THz Range

[![Open In Colab - Main](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moordrone/tlm-graphene-thz/notebooks/01_tlm_graphene_simulation.ipynb)
[![Open In Colab - Parametric](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moordrone/tlm-graphene-thz/notebooks/02_parametric_analysis.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## 📋 Description

This project implements the **Transmission Line Matrix (TLM)** method to simulate electromagnetic wave interaction with **graphene sheets** in the **terahertz (0-10 THz)** frequency range. The simulation calculates:

- **R** : Reflection coefficient
- **T** : Transmission coefficient  
- **A** : Absorption coefficient

The graphene conductivity is modeled using the **Drude model** for intraband transitions.

## 🚀 Quick Start

### Option 1: Run on Google Colab (Recommended)

Click the badges above or use these direct links:

| Notebook | Description | Link |
|----------|-------------|------|
| Main Simulation | Basic TLM simulation with graphene | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moordrone/tlm-graphene-thz/notebooks/01_tlm_graphene_simulation.ipynb) |
| Parametric Analysis | Study effect of Fermi energy and relaxation time | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moordrone/tlm-graphene-thz/notebooks/02_parametric_analysis.ipynb) |
| Simple Example | Quick demo with minimal code | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moordrone/tlm-graphene-thz/notebooks/03_simple_example.ipynb) |

### Option 2: Local Installation

```bash
# Clone the repository
git clone https://github.com/Moordrone/tlm-graphene-thz.git
cd tlm-graphene-thz

# Create virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or: venv\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt

# Run example
python examples/basic_simulation.py
```

## 📁 Project Structure

```
tlm-graphene-thz/
├── README.md
├── LICENSE
├── requirements.txt
├── setup.py
├── src/
│   ├── __init__.py
│   ├── tlm_core.py          # Core TLM functions
│   ├── graphene_model.py    # Drude model for graphene
│   ├── simulation.py        # Main simulation class
│   └── visualization.py     # Plotting utilities
├── notebooks/
│   ├── 01_tlm_graphene_simulation.ipynb
│   ├── 02_parametric_analysis.ipynb
│   └── 03_simple_example.ipynb
├── examples/
│   ├── basic_simulation.py
│   └── parameter_sweep.py
├── docs/
│   └── theory.md
└── data/
    └── results/
```

## 🔬 Physical Model

### Graphene Conductivity (Drude Model)

The intraband conductivity is given by:

$$\sigma(\omega) = \frac{e^2 E_F}{\pi \hbar^2} \cdot \frac{i}{\omega + i/\tau}$$

Where:
- $E_F$ : Fermi energy (typical: 0.1 - 1.0 eV)
- $\tau$ : Relaxation time (typical: 10 - 1000 fs)
- $\omega$ : Angular frequency
- $e$ : Electron charge
- $\hbar$ : Reduced Planck constant

### TLM Method

The TLM method discretizes space into transmission line segments. Each node performs:

1. **Scattering**: Incident pulses → Reflected pulses
2. **Connection**: Exchange pulses between adjacent nodes
3. **Boundary conditions**: PML or absorbing boundaries

The graphene sheet is modeled as a resistive boundary condition using its surface conductivity.

## 📊 Example Results

```python
from src.simulation import GrapheneTLMSimulation

# Create simulation
sim = GrapheneTLMSimulation(
    freq_range=(0.1e12, 10e12),  # 0.1 - 10 THz
    n_freq=200,
    fermi_energy=0.4,            # eV
    relaxation_time=100e-15      # 100 fs
)

# Run and plot
results = sim.run()
sim.plot_coefficients()
```

## 🛠️ Configuration

Key parameters can be adjusted:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `fermi_energy` | 0.4 eV | Graphene Fermi level |
| `relaxation_time` | 100 fs | Carrier relaxation time |
| `freq_min` | 0.1 THz | Minimum frequency |
| `freq_max` | 10 THz | Maximum frequency |
| `n_freq` | 200 | Number of frequency points |
| `n_cells` | 1000 | Number of TLM cells |

## 📚 References

1. Christopoulos, C. (1995). *The Transmission-Line Modeling Method: TLM*. IEEE Press.
2. Falkovsky, L. A. (2008). Optical properties of graphene. *Journal of Physics: Conference Series*, 129, 012004.
3. Hanson, G. W. (2008). Dyadic Green's functions and guided surface waves for a surface conductivity model of graphene. *Journal of Applied Physics*, 103(6), 064302.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For questions or suggestions, please open an issue on GitHub.

---

**Note**: Replace `YOUR_USERNAME` in the badge URLs with your actual GitHub username after creating the repository.
