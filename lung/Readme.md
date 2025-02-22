# lung
First download data from TCGA using

```bash
mkdir -p data && mv manifest.txt data/. && cd data
gdc-client download -m manifest.txt
```
Run [lung.ipynb](lung.ipynb) to preprocess data

Go trough [predictor_LUAD_LUSC.ipynb](predictor_LUAD_LUSC.ipynb) to execute the predictor discussed in the paper, this can be run on Colab or in any machine with tensorflow (possibly with GPU enabled)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1shlI-lwfH32ka9MrZ5gBCoiZrOV0YvWy/view?usp=sharing)

[model_cancer.type.h5](model_cancer.type.h5) contains the trained weights.
To reproduce our evaluation analyses load it using
```python
from tensorflow.keras.models import load_model
model = load_model(f"model_cancer.type.h5")
model.summary()
```
as described in the notebook.

Output for hierarchical stochastic block model is in the [topsbm](topsbm) folder
