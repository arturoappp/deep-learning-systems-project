# Deep Learning Systems Project — Language Identification of Short Texts with a Character-Level Transformer

## Project Description

A deep learning experiment in PyTorch, built in a single Jupyter notebook, `deep_learning.ipynb`.
The task is **text modeling with a Transformer**: identifying the language of short snippets (10 to 64 characters) among six closely related languages — Spanish, Portuguese, Italian, French, Romanian and Latin.
The baseline is a small character-level Transformer encoder; the controlled experiment changes exactly one aspect, the **encoder layer type**, replacing the Transformer layers with a bidirectional GRU while everything else (data, split, embeddings, pooling, loss, optimizer, learning rate, batch size, epochs, seed) stays the same.
Both models are evaluated on held-out chapters at four snippet lengths, with training curves, confusion matrices and misclassified examples.

**Dataset:** *A massively parallel corpus: the Bible in 100 languages* (Christodoulopoulos & Steedman, 2015), CC0 1.0 — https://github.com/christos-c/bible-corpus (pinned commit `44e5fca1bfb369a5da2ee23ebc6f421c88489c5c`).
The notebook downloads the six language files it uses (about 35 MB) into `data/raw/` on the first run; see `data/README.md`. The files are not committed because some of the underlying translations are still under copyright.

## How to Run the Project

Requirements: **Python 3.12 or newer**, Git and an internet connection for the first run (dataset download). The pinned versions in `requirements.txt` (for example `numpy==2.5.3` and `scipy==1.18.1`) do not install on Python 3.11 or older.

```bash
git clone https://github.com/arturoappp/deep-learning-systems-project.git
cd deep-learning-systems-project
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook deep_learning.ipynb
```

Then run all cells (Kernel → Restart & Run All). The notebook runs top to bottom without errors and writes three figures to `figures/`.

**GPU (optional but recommended).** `requirements.txt` pins `torch==2.11.0`, which installs a CUDA build on Linux and a CPU build on Windows from PyPI. The results in the report were produced on an NVIDIA RTX 3060 Ti, where training both models takes about 6 minutes. To use an NVIDIA GPU on Windows, install the CUDA build first:

```bash
pip install torch==2.11.0 --index-url https://download.pytorch.org/whl/cu128
pip install -r requirements.txt
```

On a CPU the notebook still runs, but training is considerably slower. The notebook seeds every random generator and enables PyTorch's deterministic algorithms; exact numbers can still differ slightly between CPU and GPU or between GPU models.

To regenerate the dependency file from the project environment:

```bash
pip freeze > requirements.txt
```

## Repository Structure

```
deep_learning.ipynb                              # data download and inspection, preprocessing, both models, evaluation, summary
Deep_Learning_Systems_Analysis_Report.pdf        # written report with in-text citations and references
requirements.txt                                 # exact package versions (pip freeze)
data/README.md                                   # dataset access instructions (files are downloaded by the notebook)
figures/                                         # fig1_training_curves, fig2_accuracy_by_length, fig3_confusion_20chars
```
