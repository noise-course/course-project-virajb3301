# Synthetic Application-Labeled Traffic Generator for pcapng

## Project Participants

| First Name | Last Name | cnet ID | Project Role |
| ---------- | --------- | ------- | ------------ |
|   Viraj    | Bodiwala  |  virajb |   Student    |

## Project Description

This project generates realistic **synthetic network traffic traces** that are already **labeled by application** (e.g., Netflix, Zoom, generic web browsing) and written directly into **pcapng** files. The problem is that ML for networking (traffic classification, QoE inference, anomaly detection) needs per-flow ground-truth labels, but real traces are private, labels are noisy, and collecting enough data per app is slow and expensive. We address this by learning the statistical behavior of real app traffic (packet sizes, inter-arrival times, burst patterns, up/down ratios, durations) and sampling new “fake” flows that closely resemble the originals; we then serialize packets to pcapng and embed labels via comment/custom option fields so tools like Wireshark or Python parsers can recover them without external CSVs. This sits squarely at the **networking × ML** intersection (synthetic data for supervised learning and model bootstrapping). Related work includes traditional traffic classification datasets and generative/simulation approaches to trace synthesis; we build a lightweight, engineering-first generator and labeling pipeline. Our goal is **research-style**: quantify realism and usefulness of synthetic traces and validate an embedding scheme that keeps labels with the packets. The quarter scope is feasible via statistical baselines (histograms/KDE/GMM) with an optional stretch to simple sequence models (LSTM/1D-CNN); known limitations (e.g., imperfect TCP dynamics, local overfitting, tool support for custom pcapng options) are documented for future work.

## Data

* Short, **controlled captures** per target application (e.g., streaming Netflix, active Zoom call, basic web browsing).
* Extracted **per-flow features**: packet size distributions, inter-arrival timing, durations, total bytes up/down, burstiness, upload/download ratios.
* Held-out **real flows** per application for evaluation (realism metrics and generalization tests).

## Deliverables

* **Python tool** that emits synthetic, application-labeled **pcapng** for a requested application (labels embedded via pcapng comment/custom option fields).
* **Example generated traces** for each supported application.
* **Evaluation report**:

  * *Realism*: distributional comparisons (e.g., KL divergence on size histograms, duration/throughput deltas, visual burst patterns).
  * *Usefulness*: train classifiers (RF/SVM/MLP) **only on synthetic flows**, test on held-out real flows (accuracy, confusion matrix).
  * *Labeling robustness*: ability to recover labels directly from pcapng without external CSVs.
* **6–8 page write-up** covering motivation, method, evaluation, limitations, and future work.
