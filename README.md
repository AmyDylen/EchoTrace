# EchoTrace


## 📌 Notice
**Source code and the PTY-C2 benchmark dataset will be released publicly after the paper is accepted.**
This repository is reserved for the publication. Once the manuscript is accepted, we will upload the full PyTorch implementation, preprocessing scripts, and PTY-C2 PCAP/annotation files.

## Abstract
Encrypted interactive tunnels can conceal PTY-based interactive shells inside long-lived flows, leaving defenders with only packet metadata and making flow-level classification prone to signal dilution. We observe that PTY activity is not uniformly distributed across a connection, but instead appears as sparse, temporally localized bursts characterized by timing, size, and direction patterns. This motivates formulating PTY-bearing encrypted interactive-traffic detection as a weakly supervised localization problem over burst-level instances rather than as a monolithic flow classification task.

To this end, we propose **EchoTrace**, a weakly supervised multiple-instance learning framework for decryption-free detection and localization of PTY-bearing encrypted interactive traffic. EchoTrace segments each connection into silence-delimited bursts, encodes burst metadata to capture temporal and directional motifs, and aggregates burst-level evidence to produce flow-level decisions while retaining instance-level relevance scores. To address label scarcity, EchoTrace is trained in two stages: self-supervised contrastive pre-training on burst metadata followed by MIL fine-tuning using only flow-level labels.

We further construct PTY-C2, a benchmark spanning TCP shells, SSH-based terminals, and TLS 1.2/1.3 encrypted interactive tunnels under diverse benign backgrounds. Extensive experiments under balanced, highly imbalanced, perturbed, and unseen-encapsulation settings show that EchoTrace consistently outperforms representative baselines in both detection and temporal traceability.

## 🧩 Method Overview
EchoTrace consists of three core components:
1. **Silence-aware burst segmentation**: Split raw encrypted flows into semantically coherent bursts based on inter-packet silence and directional transition rules.
2. **ST-MAN (Spatio-Temporal Motif Attention Network)**: Encodes packet length, direction and inter-arrival time into burst embeddings.
3. **Noisy-OR evidence aggregation**: Aggregates burst-level probabilities for flow-level prediction, preserving instance-level scores for temporal localization.

Two-stage training:
- Stage1: Contrastive self-supervised pre-training on unlabeled bursts
- Stage2: MIL fine-tuning with only weak flow-level labels

## ⚙️ Planned Environment (will be updated with code release)
