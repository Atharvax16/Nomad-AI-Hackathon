Spatial AI Reasoning using LLM
Hybrid AI system that places objects inside arbitrary 3D indoor environments using a combination of:

Deterministic geometry reasoning (collision-free placement)

Local Large Language Model (intent understanding)

Grounded explanation generation (non-hallucinated reasoning)

The model does not guess placements — it computes them and then explains why.

✨ Key Idea

Most AI interior planners hallucinate spatial logic.

This project separates responsibilities:

Component	Responsibility
Geometry Engine	Guarantees physically valid placement
LLM Planner	Converts human intent → spatial constraints
Optimizer	Finds best placement
LLM Verbalizer	Explains measured reasoning

Language decides preference
Geometry decides truth

📊 Pipeline Overview

Parse .glb room

Extract obstacles & structures

Detect semantic targets (tv, shelf, window…)

LLM converts prompt → structured plan

Candidate generation (collision-free)

Weighted scoring optimization

Grounded explanation generation

REPO STRUCTURE
Spatial-Reasoning-LLM/
│
├── main.py
├── geometry_utils.py
├── llm_planner.py
├── planner_schema.py
│
├── models/
│   └── mistral.gguf
│
├── outputs/
│   ├── plan.json
│   ├── best.json
│   ├── explanation.txt
│
├── assets/
│   └── room_scene.glb
│
├── spatial_pipeline_diagram.png
└── README.md

conda create -n spatialai python=3.10
conda activate spatialai

pip install numpy trimesh matplotlib reportlab llama-cpp-python

pip install llama-cpp-python --upgrade --force-reinstall --no-cache-dir

mistral-7b-instruct-v0.2.Q4_K_M.gguf

models/mistral.gguf

