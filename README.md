# The-DeDe-Coder
*A compendium of notes and definitions for AMS 530: Parallel Computing*

This repository was created by DeDe (TheStellarScientist) to manage the concepts covered in AMS 530 in a way that is hopefully less unwieldy than Google Docs. This repository contains all the concepts, plus links to resources, notes from further reading, and example projects. The goal is to create this as a way for the class to collaborate and digest topics in a way we understand and that will hopefully be understandable to future classes as well.

This README serves as a table of contents. The repository is organized by topics in chronological order as they are taught. Each topic has its own directory containing files that explain the concepts within.

## Repository Structure

```
/
├── 01-introduction/
├── 02-hardware-evolution-taxonomy/
├── 03-software-programming-communication/
├── 04-performance-metrics/
├── 05-algorithms/
├── 06-linear-algebra/
├── 07-differential-equations/
├── 08-molecular-dynamics/
├── 09-stochastic-optimization/
├── 10-fast-fourier-transforms/
├── resources/
│   ├── images/
│   ├── code-examples/
│   └── external-links.md
└── templates/
    └── topic-template.md
```

## Course Topics - Fall 2025

### 1. Introduction
Overview of high-performance computing (HPC), its role in scientific and engineering advancements, historical context, and future trends.

### 2. Hardware: Evolution and Taxonomy
- **Historical Context**: Evolution from vector processors to parallel systems
- **Current Systems**: Multi-core CPUs, GPUs, and other accelerators
- **Future Trends**: Quantum and neuromorphic computing
- **Taxonomy**: Classification by architecture and interconnects

### 3. Software: Programming Models and Communication
- **Programming Models**: Shared-memory (OpenMP), distributed-memory (MPI), hybrid, and PGAS approaches
- **Message Passing**: Protocols and tools for efficient inter-process communication

### 4. Performance Metrics
- **Speedup**: Performance gains
- **Efficiency**: Resource utilization and overhead
- **Scalability**: Strong and weak scaling under increased loads

### 5. Algorithms
- **Problem Decomposition**: Partitioning tasks for parallel execution
- **Communication Handling**: Minimizing latency in data exchange
- **Load Balancing**: Equitable workload distribution
- **Core CS Algorithms**: Parallel sorting, searching, and graph processing
- **Communication Patterns**: Broadcast, scatter, and gather operations

### 6. Linear Algebra
- **Matrix Operations**: Matrix-vector, matrix-matrix, dense/sparse AX=B
- **Iterative Solvers**: Jacobi, Gauss-Seidel, SOR, Conjugate Gradient
- **Advanced Methods**: Preconditioning, multigrid for elliptic PDEs

### 7. Differential Equations
- **ODEs**: Numerical integration and stability
- **PDEs**: Hyperbolic, parabolic, elliptic equations
- **Applications**: Heat, Wave, Maxwell's, and Schrödinger equations

### 8. Molecular Dynamics
- **Principles**: Modeling atomic interactions and time evolution
- **Parallelization**: Scaling simulations across distributed systems
- **Applications**: Materials science, biophysics, and chemistry

### 9. Stochastic and Optimization Methods
- **Monte Carlo**: Random sampling for integration and modeling
- **Simulated Annealing**: Optimization for complex problems
- **Genetic Algorithms**: Evolutionary search techniques

### 10. Fast Fourier Transforms
- **Theory**: Discrete Fourier transforms and complexity
- **Parallel FFTs**: Distributed and GPU-accelerated implementations
- **Applications**: Signal processing, computational physics, and data analysis

## Contributing

1. **Fork** this repository
2. **Create a branch** for your topic or improvement (`git checkout -b topic/new-concept`)
3. **Add your content** following the template in `/templates/topic-template.md`
4. **Commit your changes** (`git commit -am 'Add explanation for [concept]'`)
5. **Push to the branch** (`git push origin topic/new-concept`)
6. **Create a Pull Request**

### Content Guidelines
- Include code examples where applicable
- Add relevant images to `/resources/images/`
- Link to external resources in `/resources/external-links.md`
- Follow the established directory structure

## Quick Navigation
- [Resources](/resources/) - External links, images, and code examples
- [Templates](/templates/) - Format guidelines for new entries
- [Issues](../../issues) - Request new topics or report problems
- [Pull Requests](../../pulls) - Review proposed changes
