# Large Language Model Integration with Computational Fluid Dynamics (CFD)

**MSc Artificial Intelligence Dissertation — Brunel University London**

This project explores the integration of Large Language Models (LLMs) with Computational Fluid Dynamics (CFD) tools to automate parts of the simulation workflow, including geometry generation and simulation setup.

The research investigates whether LLMs can make CFD workflows more accessible by translating natural-language instructions into files required by engineering simulation software.

## Project Overview

Traditional CFD workflows require users to have specialized knowledge of geometry construction, mesh generation, boundary conditions, and solver configuration. This project investigates how LLMs can assist with these tasks by generating the required input files from user instructions.

Two CFD test cases were used to evaluate the approach:

* **3D Pipe Flow:** A fluid-flow simulation through a three-dimensional pipe.
* **2D Airfoil Flow:** An airflow simulation around a two-dimensional airfoil.

The project also explores fine-tuning a language model on CFD-specific data and compares its performance with an API-based LLM approach.

## System Workflow

1. The user describes the desired geometry or simulation in natural language.
2. An LLM generates a geometry file (`.geo`) or a simulation setup file (`.sif`).
3. Gmsh is used for geometry processing and mesh generation.
4. Elmer is used to run the CFD simulation.
5. The generated files and simulation behavior are evaluated for correctness and limitations.

## 📂 Repository Structure

This repository contains five Jupyter notebooks covering geometry generation, CFD simulation setup, and model fine-tuning.

| Notebook                                           | Purpose                                                          |
| -------------------------------------------------- | ---------------------------------------------------------------- |
| [`Airfoil_geo.ipynb`](./Airfoil_geo.ipynb)         | Generates the geometry definition for the 2D airfoil CFD case.   |
| [`CFD_Airfoil_sim.ipynb`](./CFD_Airfoil_sim.ipynb) | Generates the simulation setup for the airfoil case.             |
| [`CFD_Pipe_geo.ipynb`](./CFD_Pipe_geo.ipynb)       | Generates the geometry definition for the 3D pipe-flow CFD case. |
| [`CFD_Pipe_sim.ipynb`](./CFD_Pipe_sim.ipynb)       | Generates the simulation setup for the pipe-flow case.           |
| [`Fine-tune.ipynb`](./Fine-tune.ipynb)             | Contains the model fine-tuning workflow.                         |


## Technologies Used

* **Python** — implementation and workflow automation.
* **Large Language Models (LLMs)** — natural-language understanding and generation of CFD input files.
* **Meta Llama 3.1 8B** — base model used in the fine-tuning experiments.
* **LoRA (Low-Rank Adaptation)** — parameter-efficient model fine-tuning.
* **Unsloth** — model fine-tuning and optimization.
* **OpenAI API** — evaluation of API-based LLM generation.
* **Gmsh** — geometry definition and mesh generation.
* **Elmer FEM** — numerical simulation and solver execution.
* **PyVista** — mesh visualization.

## Fine-Tuning Approach

A CFD-specific question-and-answer dataset was collected and prepared to adapt a language model to domain-specific instructions.

The fine-tuning experiment used Meta Llama 3.1 8B in a 4-bit quantized configuration with LoRA. The objective was to improve the model's ability to respond to CFD-related instructions and generate relevant outputs.

The fine-tuned model was evaluated on the two CFD test cases. Its performance was compared with an API-based LLM approach to investigate the strengths and limitations of each method.

## Results and Findings

The dissertation identified several important findings:

* **Geometry generation:** LLMs showed potential for generating geometry scripts, but outputs sometimes contained errors or required correction, particularly for more complex geometries.
* **Simulation setup:** The models demonstrated the ability to generate simulation configuration files that could be used to run CFD simulations.
* **Pipe-flow case:** The simulation produced a parabolic velocity profile consistent with the expected behavior of laminar flow in a pipe.
* **Model limitations:** The fine-tuned model exhibited hallucinations and geometric inaccuracies when integrated into the workflow. API-based models showed more consistent performance in the tested tasks, although they could still omit essential information.
* **Mesh quality:** Complex geometry and mesh generation remained challenging and required further refinement.

Overall, the research demonstrates the potential of LLMs to assist with CFD workflow automation while highlighting the need for validation and human oversight.

## Limitations and Future Work

Potential areas for further development include:

* Improving the reliability of generated geometry files.
* Enhancing mesh quality, particularly for complex geometries.
* Ensuring that the model requests missing parameters before generating files.
* Introducing automated validation of generated scripts and simulation inputs.
* Exploring hybrid approaches that combine LLMs with conventional engineering tools.

## Academic Context

This project was completed as part of the MSc in Artificial Intelligence at Brunel University London during the 2023–2024 academic year.

**Dissertation title:** *Large Language Model Integration with Computational Fluid Dynamics*

**Author:** Mohamed Khaled Hamza

**Supervisor:** Dr Weibo Liu
