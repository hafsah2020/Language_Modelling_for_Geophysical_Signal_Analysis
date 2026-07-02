# Language Modelling for Well Signal Analysis

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


## Data Sources

- [Equinor Volve Dataset](https://www.equinor.com/energy/volve-data-sharing)
- [FORCE 2020 ML Competition](https://github.com/bolgebrygg/Force-2020-Machine-Learning-competition)
- [SEG 2016 Facies Classification Challenge](https://github.com/seg/2016-ml-contest)

---

*Personal learning repository. Course curriculum © Google DeepMind.*
