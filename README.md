# Semantic Communication System with RL, VQ-VAE, and NVIDIA Sionna

**Main Focus: Implementation of Semantic QAM.** This repository provides the official implementation for a custom physical layer constellation where symbols are positioned based on their semantic importance, deeply integrating Vector Quantized-Variational Autoencoders (VQ-VAE) with NVIDIA Sionna.

## Overview
This repository provides a joint semantic-physical layer framework for adaptive data transmission over Additive White Gaussian Noise (AWGN) channels. Unlike standard systems that treat constellation design and semantic encoding as independent problems, this framework directly links them. It utilizes an importance-weighted VQ-VAE to extract discrete latent concepts, a Semantic Criticality Indicator (SCI) to score task relevance, and a Deep Reinforcement Learning (DRL) agent to dynamically adapt the payload based on instantaneous channel conditions.

## Key Features
* **Learned Semantic M-QAM Constellation:** Replaces standard Gray-coded QAM grids by assigning physical constellation points based on joint co-occurrence statistics and semantic importance scores.
* **Importance-Weighted VQ-VAE (IW-VQ-VAE):** A core compression engine that jointly learns discrete semantic representations and their task relevance via a differentiable downstream classifier.
* **Adaptive DRL Rate Controller:** A Deep Q-Network (DQN) agent that observes normalized channel SNR and dynamically selects the optimal Top-K concepts to transmit, balancing bandwidth efficiency and task accuracy.
* **Novel Evaluation Metrics:** Includes full code to calculate Semantic Symbol Vulnerability (SSV), Importance-Weighted SSV (IW-SSV), and Smart Protection Probability (SPPR) to evaluate semantic robustness at the physical layer.
* **Cross-Domain Applicability:** Built to support multiple modalities, including MNIST, Fashion-MNIST, and the Free Spoken Digit Dataset (FSDD).

## File Description
* `Semantic_QAM_21_April_2026.ipynb`: The main Jupyter Notebook containing the end-to-end pipeline. This includes data generation/processing (e.g., FSDD audio to spectrograms), IW-VQ-VAE training, RL agent setup, and physical layer evaluation using Sionna.

## How to Run
1. Ensure all dependencies are installed (see the **Dependencies** section below).
2. If using the FSDD audio dataset, clone it to your local directory: 
   `git clone https://github.com/Jakobovski/free-spoken-digit-dataset.git`
3. Open `Semantic_QAM_21_April_2026.ipynb` in your preferred notebook environment (e.g., Jupyter Notebook, VS Code).
4. Modify the configurable parameters at the top of the notebook to suit your experiment.
5. Run the notebook sequentially from top to bottom. It will automatically process the data, train the VQ-VAE, set up the RL agent, and evaluate the Semantic QAM system across different SNRs.

## Configurable Variables
You can easily change the behavior of the experiment by modifying these global variables in the notebook:

### Dataset Options
* `DATASET_NAME`: The master toggle for selecting the dataset. Options include: `'fashion_mnist'`, `'mnist'`, `'kmnist'`, `'cifar10'`, `'svhn'`, `'mnist_corrupted'`, `'kannada_mnist'`, and `'fsdd'` (audio).
* `digit_list`: A list of classes/digits you want to include in the dataset (default: `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`).
* `n_train` / `n_test`: The number of training and testing samples to use (adjusts automatically for smaller datasets like FSDD).

### Experiment Parameters
* `list_QAM_ORDER`: The list of QAM orders (in bits per symbol) to simulate and evaluate (e.g., `[2, 4, 6, 8, 10]` for 4-QAM up to 1024-QAM).
* `snr_values`: The range of Signal-to-Noise Ratio (SNR) values in dB to test the channel across (e.g., `list(range(-10, 20, 2))`).

### Training Parameters
* `total_epochs`: Total epochs for VQ-VAE representation learning.
* `semantic_start_epoch`: The epoch number at which the semantic downstream task loss activates.
* `BATCH_SIZE`: The batch size for neural network training.
* `STEPS`: Total number of training steps for the Semantic QAM physical layer module.
* `EPISODES`: Total episodes for training the DRL rate controller agent.

## Dependencies
* `tensorflow` >= 2.13
* `sionna-no-rt` == 1.2.1
* `librosa` (for audio datasets)
* `numpy`, `matplotlib`, `scipy`

## Citation
If you use this code in your research, please cite our paper:
```bibtex
@inproceedings{shaju2026semantic,
  title={Not All Concepts Are Equal: Importance-Aware Constellation Design for Semantic Communications},
  author={Albert Shaju, Christo Kurisummoottil Thomas, Mayukh Roy Chowdhury},
  booktitle={IEEE Global Communications Conference (GLOBECOM)},
  year={2026}
}