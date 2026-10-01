DASE7506 MP1 - Small Language Model Challenge

Student Name: Gu zheye
Student ID: 3036708256
Final Test BPB: 1.71183

Repository Overview

This repository contains the code, final model checkpoint, evaluation results, and report for MP1.

- code/: Source code (model.py, train.py, evaluate.py, common.py)
- checkpoint.pt: Final trained model weights (1.71183 BPB)
- test_cpu_fp32.json: Full test evaluation result
- REPORT.md: Project report (method, experiments, ablation, analysis)

How to Reproduce

To evaluate the final checkpoint on the full test split, run:

python evaluate.py --checkpoint checkpoint.pt --device cpu --precision fp32 --split test

AI Assistance Disclosure

AI assistance was used for environment setup, command-line debugging, and drafting the report. All code, training, and results are my own.
