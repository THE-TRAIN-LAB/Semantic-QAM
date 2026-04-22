# Semantic Communication System with RL, VQ-VAE, and SIONNA

**Main Focus: Implementation of Semantic QAM.** This repository provides the code for a custom constellation where symbols are positioned based on the semantic importance of each symbol, integrating VQ-VAE and SIONNA.

## Overview


## Key Features


## File Description
- `Semantic_QAM_21_April_2026.ipynb`: Main Jupyter Notebook containing the full pipeline, from data generation (e.g., FSDD audio to spectrogram processing), VQ-VAE 

## How to Run
1. Ensure all dependencies are installed (see **Dependencies** section).
2. If using the FSDD audio dataset, clone it to your local directory: `git clone https://github.com/Jakobovski/free-spoken-digit-dataset.git`.
3. Open `Semantic_QAM_21_April_2026.ipynb` in your preferred notebook environment (e.g., Jupyter Notebook, VS Code).
4. Modify the configurable parameters at the top of the notebook to suit your experiment.
5. Run the notebook sequentially from top to bottom. It will automatically process the data, train the VQ-VAE, set up the RL agent, and evaluate the Semantic QAM system across different SNRs.

## Configurable Variables
You can easily change the behavior of the experiment by modifying these variables in the notebook:

### Dataset Options
- `DATASET_NAME`: The master toggle for selecting the dataset. Options include: `'fashion_mnist'`, `'mnist'`, `'kmnist'`, `'cifar10'`, `'svhn'`, `'mnist_corrupted'`, `'kannada_mnist'`, and `'fsdd'` (audio).
- `digit_list`: A list of classes/digits you want to include in the dataset (default: `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`).
- `n_train` / `n_test`: The number of training and testing samples to use (adjusted automatically for smaller datasets like FSDD).

### Experiment Parameters
- `list_QAM_ORDER`: The list of QAM orders to simulate and evaluate (e.g., `[2, 4, 6, 8, 10]`).
- `snr_values`: The range of Signal-to-Noise Ratio (SNR) values to test the channel across (e.g., `list(range(-10, 20, 2))`).

### Training Parameters
- `total_epochs`: Total epochs for VQ-VAE training.
- `semantic_start_epoch`: The epoch number at which semantic positioning starts.
- `BATCH_SIZE`: The batch size for model training.
- `STEPS`: Total number of training steps for the Semantic QAM module.
- `EPISODES`: Total episodes for training the RL agent.

## Dependencies
- `tensorflow` >= 2.13
- `sionna-no-rt` == 1.2.1
- `librosa`
- `numpy`, `matplotlib`, `scipy`

## Author
Albert Shaju, Christo Kurisummoottil Thomas
*April 2026*
