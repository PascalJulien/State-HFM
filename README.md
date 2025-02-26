# State-HFM: Path Planning for Autonomous Four-Wheel Steering Forklifts

This repository implements a path planning framework based on the Hamiltonian Fast Marching Method (HFMM) with state-based control for autonomous vehicles with four-wheel steering capabilities. The framework provides efficient and collision-free trajectories in both confined and open spaces

## Key Features

- **Enhanced maneuverability**: Full support for four-wheel steering (4WS) capabilities, enabling complex maneuvers in tight spaces
- **State-based planning**: Incorporates different operational states (forward/backward navigation, specialized maneuvering, crab walk,...)
- **Smooth trajectory generation**: Produces naturally smooth paths with optimized curvature and fewer unnecessary direction changes
- **Deterministic results**: Unlike sampling-based approaches, delivers consistent and reliable trajectories
- **Comprehensive benchmarking**: Comparative analysis against state-of-the-art sampling-based planners (RRT, RRT*, Informed-RRT*, SST)

## System Requirements

- Python 3.7+
- CUDA-enabled GPU (required for efficient Fast Marching computation)
- CUDA libraries and supporting toolkit
- NumPy, SciPy, Matplotlib, Cupy

## Installation

### 1. Clone the repository with submodules

```bash
git clone https://github.com/PascalJulien/State-HFM.git
cd State-HFM
git submodule init && git submodule update
```

### 2. Install AGD (Adaptive Grid Discretization)

The State-HFM implementation relies on the AGD library for the Fast Marching Method implementation. 

```bash
pip install agd
```

### 3. Set up bench-mr for benchmarking

The benchmarking framework requires additional dependencies:

```bash
cd bench-mr
pip install -r python/requirements.txt
```

Build the benchmarking tool : 
```bash
mkdir build
cd build
cmake ..
cmake --build . -- -j4
```

## Project Structure

The repository contains two main Jupyter notebooks:

### `State_HFM_description.ipynb`

This notebook provides a detailed explanation of the Hamiltonian Fast Marching Method with state-based control, including:

- Mathematical foundation of the approach
- Four-wheel steering kinematic model
- Robot shape approximation using multiple balls
- Implementation of state-based controls
- Configuration space construction
- Visualization of planning results

### `State_HFM_benchmark.ipynb`

This notebook presents a comprehensive benchmarking framework for evaluating path planning algorithms, including:

- Comparison of State-HFM against sampling-based planners (RRT, RRT*, Informed-RRT*, SST)
- Performance evaluation on both predefined and procedurally generated environments
- Metrics calculation for path efficiency, smoothness, and safety
- Quantitative analysis of results
- Visualization of computed trajectories

## Usage

1. Open the Jupyter notebooks:

```bash
jupyter notebook
```

2. Start with `State_HFM_description.ipynb` to understand the algorithm implementation.
3. Explore `State_HFM_benchmark.ipynb` to compare performance against other planners.

## Performance Metrics

The benchmarking framework evaluates path planning algorithms using several key metrics:

- **Path Length**: Total distance traveled
- **Angle Over Length (AOL)**: An alternative measure of path smoothness
- **Normalized Curvature**: Curvature scaled by path length
- **Maximum Curvature**: Highest rate of turning along the path
- **Minimum Clearing Distance**: Smallest distance to obstacles (safety metric)
- **Mean Clearing Distance**: Average clearance throughout trajectory

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- The implementation builds upon the [AGD library](https://github.com/Mirebeau/AdaptiveGridDiscretizations) developed by Jean-Marie Mirebeau for Fast Marching Method implementations
- The benchmarking framework extends the [Motion Planning Benchmark](https://github.com/robot-motion/bench-mr) system developed by Eric Heiden, Luigi Palmieri, Leonard Bruns, and Ziang Liu

<!--## Citation

If you use this code in your research, please cite:

```
@misc{StateBased_HFM,
  author = {Your Name},
  title = {State-HFM: Path Planning for Autonomous Four-Wheel Steering Forklifts},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/PascalJulien/State-HFM}}
}
```-->
