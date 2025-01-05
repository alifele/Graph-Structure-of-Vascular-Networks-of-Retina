
# 🕸️ Vascular Network Graphs of the Human Retina

This repository contains the vascular network graphs of the human retina, stored in the [NetworkX](https://networkx.org/) graph format. These graphs represent the vascular structures of the retina and are suitable for analysis, visualization, and research in graph theory, vascular biology, and more.

---

## 📖 Table of Contents
- [🖍 Introduction](#-introduction)
- [📊 Dataset Overview](#-dataset-overview)
- [📖 Example Usage](#-example-usage)
  - [📥 Loading and Saving Data](#-loading-and-saving-data)
  - [🔢 Graph Matrices](#-graph-matrices)
  - [🔍 Edge Iteration and Plotting](#-edge-iteration-and-plotting)
  - [🔁 Extracting and Plotting Cycles](#-extracting-and-plotting-cycles)
- [🔗 How to Cite](#-how-to-cite)
- [💡 Contributions](#-contributions)

---

## 🖍 Introduction
This repository provides a dataset of vascular networks extracted from the human retina. The graphs are saved in the [NetworkX](https://networkx.org/) format, enabling easy manipulation and analysis. Each edge in the graph is associated with a curve, represented as weights, making it possible to reconstruct the vascular structure geometrically.

---

## 📊 Dataset Overview
Here’s a visual representation of the dataset elements:

![Dataset Figure](https://github.com/alifele/Graph-Structure-of-Vascular-Networks-of-Retina/blob/2f6f0e53482d7428857be17bc566f8fddb5480c1/images/ROSE-O-Train.png)  
*Figure: Visual depiction of the vascular network.*

---

## 📖 Example Usage

### 📥 Loading and Saving Data
```python
import networkx as nx

# Load the graph from a file
G = nx.read_gpickle("vascular_network.gpickle")

# Save the graph to a file
nx.write_gpickle(G, "output_network.gpickle")
```

---

### 🔢 Graph Matrices
Calculate important graph matrices, such as the incidence matrix:
```python
import networkx as nx
import numpy as np

# Incidence matrix
def incidence_matrix(graph):
    return nx.incidence_matrix(graph).toarray()

# Example usage
G = nx.read_gpickle("vascular_network.gpickle")
inc_matrix = incidence_matrix(G)
print(inc_matrix)
```

---

### 🔍 Edge Iteration and Plotting
Iterate over edges and plot the graph:
```python
import matplotlib.pyplot as plt

# Iterate over edges and plot the graph
for u, v, data in G.edges(data=True):
    curve = data['weight']  # Assuming 'weight' holds the curve (x, y) coordinates
    x, y = zip(*curve)
    plt.plot(x, y, label=f"Edge ({u}, {v})")

plt.legend()
plt.show()
```

---

### 🔁 Extracting and Plotting Cycles
Extract cycles and visualize them as closed loops:
```python
import networkx as nx
import matplotlib.pyplot as plt

# Extract cycles
cycles = nx.cycle_basis(G)

# Plot each cycle
for cycle in cycles:
    cycle_coords = []
    for i in range(len(cycle)):
        u, v = cycle[i], cycle[(i+1) % len(cycle)]  # Wrap around to the start
        if G.has_edge(u, v):
            curve = G[u][v]['weight']  # Assuming 'weight' holds the curve
            cycle_coords.extend(curve)
    x, y = zip(*cycle_coords)
    plt.plot(x, y, label="Cycle")

plt.legend()
plt.show()
```

---

## 🔗 How to Cite
If you use this dataset in your research or application, please cite the following paper:

> The citation information will be made available soon.

---

## 💡 Contributions
We welcome contributions! If you have suggestions, improvements, or bug fixes, feel free to submit a pull request or open an issue.  

📩 For any queries or feedback, please reach out to [Your Contact Information or Email].

---

🎉 **Thank you for using this dataset! Happy graphing!**
