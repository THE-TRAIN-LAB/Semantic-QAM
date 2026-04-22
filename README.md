# Semantic Communication System with RL, VQ-VAE, and SIONNA

This repository contains the implementation of a comprehensive semantic communication system combining Reinforcement Learning (RL), Vector Quantized Variational Autoencoders (VQ-VAE), and the SIONNA library for realistic wireless channel simulations. 

## Overview
The system dynamically adapts the semantic concept transmission over varying Signal-to-Noise Ratios (SNRs). It integrates:
- **VQ-VAE** for efficient semantic concept learning and representation.
- **Reinforcement Learning (DQN)** for adaptive concept selection and rate control.
- **SIONNA** for simulating realistic wireless physical layer properties.
- **Task-based Semantic Quality Measurement**, evaluating performance based on downstream task accuracy (classification) rather than traditional pixel-level MSE.

## Key Features
- **Dynamic Rate Control:** Uses an RL agent to adjust the bits-per-concept based on channel conditions.
- **Multi-SNR Evaluation:** Comprehensive testing and plotting of system performance across a range of SNR values.
- **Cross-Layer Design:** Joint optimization of the semantic representations and the physical layer transmission strategy.

## File Description
- `Semantic_QAM_21_April_2026.ipynb`: Main Jupyter Notebook containing the full pipeline, from data generation (e.g., FSDD audio to spectrogram processing), VQ-VAE training, RL agent setup, to final evaluation over the SIONNA-simulated channel.
- `QAM_order_based_bit_per_concept_Sem_QAM_April_6_2026.ipynb`: Alternative implementation focusing on QAM-order-based rate adaptation.
- `*.csv`: Result files logging the performance metrics across different scenarios.

## Dependencies
- `tensorflow` >= 2.13
- `sionna-no-rt` == 1.2.1
- `librosa`
- `numpy`, `matplotlib`, `scipy`

## Author
Albert Shaju, Christo Kurisummoottil Thomas
*April 2026*
