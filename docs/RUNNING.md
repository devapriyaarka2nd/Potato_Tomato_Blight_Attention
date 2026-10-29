# Running the supplied notebook

This package organizes the historical code; it does not repair or retrain it. Read `CODE_REVIEW.md` first.

## Environment

The original notebook expects Google Colab, Google Drive, TensorFlow/Keras, NumPy, Matplotlib, scikit-learn, Seaborn, and Pillow. `google.colab` is supplied by Colab, so it is intentionally not added to the general requirements file. Original tested versions are unknown.

`requirements.txt` is an inferred dependency list, not a validated lockfile. Select a Python version supported by your TensorFlow build and check compatibility with the notebook's `ImageDataGenerator` and Lambda serialization.

## Paths and prerequisites

| Original location | Purpose |
| --- | --- |
| `/content/drive/MyDrive/PlantVillage` | Two potato class folders used for training/validation and the later selected subset |
| `/content/drive/MyDrive/filtered_dataset` | Separate folder assumed by the historical evaluation cell |
| `/content/drive/MyDrive/potato_disease_classifierattention.keras` | External saved model loaded by visualization/evaluation cells |
| `model_path` | Undefined variable in original cell 2; must be resolved to the intended trusted model |

The dataset, filtered directory, and model file are not included.

## Colab use

1. Open `notebooks/potato_attention_cnn.ipynb` in Colab.
2. Mount your Drive with the first original code cell.
3. Verify the exact datasets and saved model correspond to the experiment you intend to inspect.
4. Review all absolute paths, class names, and the undefined model path before running dependent sections.


## Local use

Create a virtual environment and install requirements as shown in the root README. Launch Jupyter from the repository root. Skip the Colab mount cell and replace all Drive paths with local paths; do not assume updating one path changes the repeated path definitions elsewhere.

You may keep the data under `data/PlantVillage/` and weights under `models/` locally; both locations are excluded from Git. The notebook does not automatically resolve these locations.

## Saving results after a verified run

Record code revision, model hash, dataset identity, class map, image IDs, preprocessing, split, and metric averaging with every result. Save trained weights before later cells overwrite the `model` variable. This organizational package leaves the historical code unchanged; any execution repair should be reviewed and recorded separately.
