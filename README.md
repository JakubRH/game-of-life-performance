# Game of Life Performance Benchmarks in Python

A collection of Conway's Game of Life implementations in Python, comparing performance across different optimization techniques (2025).

The goal is to simulate a **4096 × 4096 grid** over **10,000 generations** and measure execution time on modern hardware.

## Implementations Included

- Pure Python (baseline)
- Numba CPU (with `prange` parallelization)
- Numba CUDA (basic GPU kernel)
- Numba CUDA with shared memory optimization
- Taichi (GPU-accelerated, Python-like syntax)
- CuPy (GPU convolution using `roll` operations)
- HashLife algorithm (via `python-lifelib`)

## Results (example on RTX 4070 Laptop, December 2025)

| Implementation              | Time (seconds) | Speedup vs Pure Python |
|-----------------------------|----------------|------------------------|
| Pure Python                 | >1800          | 1×                     |
| Numba CPU (parallel)        | ~15–20         | ~100×                  |
| Numba CUDA (basic)          | ~0.5–0.6       | ~3000×                 |
| Numba CUDA (shared memory)  | ~0.15–0.20     | ~10,000×               |
| **Taichi (GPU)**            | **~0.12–0.18** | **~12,000×**           |
| CuPy (roll + fuse)          | ~0.25–0.35     | ~6000×                 |
| HashLife (python-lifelib)   | ~3–8           | ~300×                  |

> **Winner**: Taichi — best combination of performance and code readability.

## Requirements

- Python 3.10+
- NVIDIA GPU recommended for GPU versions
- See `environment.yml` for full dependencies

```yaml
name: gol-benchmark
dependencies:
  - python=3.10
  - numpy
  - numba
  - taichi
  - cupy
  - python-lifelib
  - jupyter
  - matplotlib
  - pandas
