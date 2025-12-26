# Conway's Game of Life – Performance Benchmarks in Python

This repository presents several implementations of Conway's Game of Life in Python, focusing on performance comparison across different optimization techniques.

## What is Conway's Game of Life?

Conway's Game of Life is a zero-player cellular automaton created by mathematician John Horton Conway in 1970. It takes place on an infinite two-dimensional grid of square cells, each of which is either alive or dead.

The state of the grid evolves in discrete generations according to four simple rules based on the number of live neighbors (using the Moore neighborhood – the 8 surrounding cells):

- **Underpopulation**: A live cell with fewer than 2 live neighbors dies.
- **Survival**: A live cell with 2 or 3 live neighbors survives to the next generation.
- **Overpopulation**: A live cell with more than 3 live neighbors dies.
- **Reproduction**: A dead cell with exactly 3 live neighbors becomes alive.

Despite its simplicity, the Game of Life can produce remarkably complex and emergent behavior, making it a popular subject for studying computation, emergence, and algorithmic efficiency.

## Benchmark Setup

All implementations simulate a grid of **1000 × 1000 cells** over **10,000 generations**.  
Tests were performed on a Gigabyte G5 GD laptop (11th Gen Intel Core i5-11400H @ 2.70 GHz, NVIDIA RTX 3050 GPU).

## Implementations Included

- Pure Python (baseline, list-based)
- Numba CPU (single-threaded with `@njit`)
- Numba CPU with multi-threading (`prange`)
- Numba CUDA (basic GPU kernel)
- Taichi (GPU-accelerated, high-level syntax)
- CuPy + SciPy convolution (hybrid CPU/GPU approach)

## Usage

Open `benchmark.ipynb` in Jupyter Notebook or JupyterLab.  
Each section contains a complete implementation with timing measurement. Run the cells sequentially to reproduce the results.

The notebook includes code explanations and discussion of trade-offs between readability and performance.

## License

MIT License – feel free to use, modify, and share.

## Author

Jakub Hryc, PhD  
Computational Biology & Scientific Computing

December 2025
