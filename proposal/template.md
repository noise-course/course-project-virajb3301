# ML/Net Leaderboard: Reproducing & Extending ML for Networking with nPrint/pcapML

## Project Participants

| First Name | Last Name | cnet ID | Project Role |
| ---------- | --------- | ------- | ------------ |
| Viraj      | Bodiwala  | virajb  | Lead         |

## Project Description

This project builds a **reproducible ML/Net leaderboard** using **nPrint** and **pcapML** to **re-produce or extend** the best-known results across classic ML-for-networking tasks (traffic classification, QoE inference, anomaly detection, encrypted flow ID). The core problem is that results are hard to compare due to fragmented datasets, inconsistent feature extraction, and non-reproducible pipelines. This matters because networking operations and security increasingly rely on ML; without apples-to-apples benchmarking, reported gains can be noisy or non-transferable. We will follow the nPrint leaderboard directions, standardize data prep and feature generation with nPrint/pcapML, and evaluate models under rigorous splits (random, cross-capture/network, temporal). This sits squarely at the **networking × ML** intersection, emphasizing clean feature representations, reproducibility, and generalization. Related work includes the nPrint leaderboard, pcapML/NetML libraries, and prior SOTA papers; our contribution is a documented reproduction plus targeted extensions (feature variants, stronger evaluation splits, lightweight model improvements). The goal is **research-style reproducibility with extensions**: match reported numbers where possible, explain discrepancies, and push robustness or accuracy in at least one task with modest, well-justified changes.

## Data

* Public packet/flow traces linked from the **nPrint leaderboard** and compatible with **nPrint/pcapML** (labeled app/QoE tasks where available).
* Derived **packet/flow features** via nPrint (signatures) and pcapML tensors/tables.
* Evaluation splits: **random (in-distribution)**, **cross-capture / cross-network**, and **temporal (train-past/test-future)**.

## Deliverables

* **Clean Jupyter notebook** (restart-and-run-all) that downloads/preps data, runs nPrint/pcapML, trains models, and reports results.
* **Project report (Sphinx)** with clear, portfolio-quality documentation and inline code/configs (Conda/Docker, seeds, exact CLI).
* **Leaderboard table** comparing reproduced results vs. reported results and our extensions (accuracy/F1/AUROC, variance across seeds/splits).
* **Ablations & analysis**: impact of feature representations, split choice, and simple model changes (e.g., RF/SVM/MLP vs. small 1D-CNN/Transformer).
* **One-click environment** (Conda/Docker + Makefile/CLI) and pointers to any required datasets.
