# Language Modelling for Well Log Interpretation

Personal study notes following the [Google DeepMind Language Modelling course](https://www.skills.google/collections/deepmind) on Google Skillboost. Each module is worked through with well log interpretation as the applied context.

---

## Repository Structure

```
.
├── data/
│   ├── raw/                  # LAS files and formation tops
│   └── processed/            # Normalised, windowed datasets
│
├── notebooks/
│   ├── 01_probability_distributions/
│   ├── 02_ngrams/
│   ├── 03_ngram_vs_transformer/
│   ├── 04_dataset_preparation/
│   ├── 05_train_slm/
│   ├── 06_preprocessing/
│   ├── 07_character_word_tokenization/
│   ├── 08_subword_tokenization/
│   ├── 09_bpe_tokenizer/
│   ├── 10_embeddings/
│   ├── 11_slm_with_bpe/
│   ├── 12_signal_vs_noise/
│   ├── 13_single_layer_nn/
│   ├── 14_complex_data_separation/
│   ├── 15_mlp_design/
│   ├── 16_hyperparameter_tuning/
│   ├── 17_overfitting/
│   ├── 18_gradients/
│   ├── 19_keras_training/
│   ├── 20_attention_weights/
│   ├── 21_attention_mechanism/
│   ├── 22_masked_multihead_attention/
│   ├── 23_positional_embeddings/
│   └── 24_transformer_parameters/
│
└── src/
    ├── tokenizers/
    ├── models/
    └── utils/
```

---

## Modules

### Part 1 — Foundations

| # | Module | Well Log Application |
|---|--------|----------------------|
| 01 | **Create Your Own Probability Distribution** | **Well Log Uncertainty Quantification.** Assign probability distributions over lithofacies (sandstone, shale, limestone, etc.) given log readings (GR, RHOB, NPHI, RT). Covers: hand-coding a facies posterior, Monte Carlo sampling with `random.choices` to generate geological realisations, propagating classification uncertainty into porosity P10/P50/P90, context-shifting (low-GR sand vs. high-GR shale), variance decomposition across measurement/model/geological uncertainty sources, sequential depth-column interpretation, and temperature scaling as an analogue for data-quality confidence. |
| 02 | **Experiment with N-grams** | Treat discretised log sequences as "text". Build N-gram models to predict the next depth interval's facies from the previous N intervals. |
| 03 | **Compare N-gram and Transformer Language Models** | Compare N-gram facies prediction against a small transformer on the same well log sequence. |
| 04 | **Prepare the Dataset for Training an SLM** | Curate a multi-well LAS dataset: align depths, handle missing curves, split into train/val/test by well. |
| 05 | **Train Your Own Small Language Model** ⭐ | Train an SLM end-to-end to predict continuous log curves (e.g. predict DT from GR + RHOB + NPHI). Evaluate on a blind well. |

### Part 2 — Tokenization

| # | Module | Well Log Application |
|---|--------|----------------------|
| 06 | **Preprocess Data** | Normalise log curves (depth alignment, despiking, null removal). Convert LAS files to structured arrays. |
| 07 | **Tokenize Texts into Characters and Words** | Discretise log values into depth tokens (characters = single samples; words = depth windows). |
| 08 | **Tokenize Texts into Subword Tokens** | Apply BPE-style grouping to log sequences. Discover recurring log patterns (e.g. coarsening-upward cycles) as "subword" tokens. |
| 09 | **Implement a BPE Tokenizer** | Implement Byte-Pair Encoding from scratch on discretised log sequences. Visualise merged patterns and their geological meaning. |
| 10 | **Experiment with Embeddings** | Learn dense embeddings for log facies tokens. Visualise with UMAP/t-SNE — do geologically similar facies cluster together? |
| 11 | **Train an SLM with Your BPE Tokenizer** | Re-train the SLM from Module 05 using the custom BPE tokenizer. Compare against character-level tokenization. |

### Part 3 — Neural Network Fundamentals

| # | Module | Well Log Application |
|---|--------|----------------------|
| 12 | **Distinguish Between Signal and Noise** | Apply signal processing (moving average, Savitzky-Golay) to noisy resistivity logs. Distinguish real bed boundaries from tool noise. |
| 13 | **Make Predictions with a Single-Layer Neural Network** | Classify clean sand vs. shale from GR alone. Examine the decision boundary. |
| 14 | **Separate More Complex Data** | Add RHOB + NPHI. Show why a linear model fails for carbonate vs. clastic separation. |
| 15 | **Design Your Own MLP** | Multi-layer perceptron for multi-class lithofacies prediction (shale, sand, carbonate, coal). |
| 16 | **Tune Hyperparameters** | Grid/random search over learning rate, batch size, and hidden units. Use a validation well. |
| 17 | **Mitigate Overfitting** | Dropout, L2 regularisation, and early stopping on small well datasets. |
| 18 | **Gradients** | Visualise gradient flow. Explore vanishing gradients when stacking many layers on log data. |
| 19 | **Train Your Model with Keras** | MLP in Keras with ModelCheckpoint, EarlyStopping, TensorBoard callbacks. |

### Part 4 — Transformers

| # | Module | Well Log Application |
|---|--------|----------------------|
| 20 | **Visualising Attention Weights** | Visualise which depth intervals the model attends to when predicting a bed boundary. |
| 21 | **Implement the Attention Mechanism** | Scaled dot-product attention from scratch on a sequence of log depth windows. |
| 22 | **Implement Masked Multi-Head Attention** | Causal masking for autoregressive log curve prediction. |
| 23 | **Positional Embeddings** | Sinusoidal and learned positional embeddings for depth sequences. |
| 24 | **Trainable Parameters in the Transformer Model** | Count every trainable parameter. Relate model size to dataset size and overfitting risk. |

---

## Data Sources

- [Equinor Volve Dataset](https://www.equinor.com/energy/volve-data-sharing)
- [FORCE 2020 ML Competition](https://github.com/bolgebrygg/Force-2020-Machine-Learning-competition)
- [SEG 2016 Facies Classification Challenge](https://github.com/seg/2016-ml-contest)

---

*Personal learning repository. Course curriculum © Google DeepMind.*
