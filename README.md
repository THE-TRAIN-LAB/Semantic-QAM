# Semantic Communication System with RL, VQ-VAE, and NVIDIA Sionna

**Main Focus: Implementation of Semantic QAM.** This repository provides the official implementation for a custom physical layer constellation where symbols are positioned based on their semantic importance, deeply integrating Vector Quantized-Variational Autoencoders (VQ-VAE) with NVIDIA Sionna.

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