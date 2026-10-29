# Code and reproducibility review

This static review concerns the uploaded `Potato_CNN_Attention.ipynb` and `1810.pdf`. It does not establish that this exact notebook/checkpoint produced every paper result. All seven code cells are preserved in the organized notebook. No experiment was rerun or silently corrected.

References below use **zero-based cell indices in the original notebook**. The organized notebook adds Markdown sections, so use section headings rather than assuming cell indices are unchanged.

## Coverage and model terminology

The paper covers both potato and tomato. Original cell 1 explicitly trains only on `Potato___Early_blight` and `Potato___Late_blight`, and its classifier has two outputs. The tomato experiment is not presented here.

The function named `tri_attention` implements parallel channel refinement and spatial refinement, followed by additive fusion. It should not be described as three independently learned attention branches. 

## Saved result provenance needs reconciliation

- Cell 1 records 1,600 training and 400 validation images, then prints `Validation Loss: 0.0360, Validation Accuracy: 0.9925`.
- Cell 2 loads an external model via `model_path` and evaluates the validation subset of a separate `filtered_dataset`. Its saved report has 400 samples and rounded accuracy 0.55. Its saved confusion matrix is `[[200, 0], [181, 19]]`.
- Cell 6 reloads a `.keras` model from Drive and evaluates up to 150 images per class. Its saved report has 300 samples and rounded accuracy 0.66.
- The manuscript reports potato training/validation accuracy 99.47%/99.25% and separately reports precision/recall/F1 as 0.93/0.92/0.92. 


## Execution order and external files

Cell 2 uses `model_path`, but no supplied cell defines it. Cells 3, 4, and 6 load `/content/drive/MyDrive/potato_disease_classifierattention.keras`. That file was not provided.

The explicit save step is cell 5, after several cells that load and overwrite `model`. As written, that save may save the previously loaded external model rather than the model just trained in cell 1. A fresh top-to-bottom run cannot complete without external files and a defined model path. A repaired version should identify and save the training checkpoint before loading it elsewhere; such a repair would be a separate, documented code change.

The notebook uses Lambda with `spatial_avg_pool_fn`. Verify function registration/custom-object handling and compatibility with the exact TensorFlow/Keras version used to save the trusted model. Providing custom objects does not establish that loading was tested. No deserialization safety settings were changed in this package.

## Validation augmentation and callback behavior

Cell 1 uses the same `ImageDataGenerator` configuration, including random transformations, for both training and validation. Repeated validation can therefore differ even for the same model. Validation is also observed during model development; it is not an independent final test set.

`EarlyStopping` and `ReduceLROnPlateau` objects are defined, but `model.fit` receives neither through `callbacks=`. They do not affect that training call. Do not describe early stopping, learning-rate scheduling, or best-weight restoration as active in this snapshot.



## Final subset is not established as an independent test set

Cell 6 selects the first up-to-150 readable, sorted files in each of the same potato class directories used for the earlier training/validation setup. It does not exclude training or validation filenames. 

## Attention visualization

Cells 3 and 4 are two visualization variants. They read `multiply` and `multiply_1`, which are attention-refined features rather than raw channel/spatial attention weights. 

Cell 4 normalizes by `max - min` without guarding constant feature maps. Averaging channels is a visualization choice, not evidence that the model localizes lesions correctly.

## Reproducibility details to supply

1. The exact potato and tomato training versions used for each paper result.
2. Trusted saved model files, training configuration, and class-index mappings.
3. Dataset source/export/version and train/validation/test image-ID manifests.
4. TensorFlow, Keras, Python, and other dependency versions.
5. Original metric exports with checkpoint and subset identity.
6. A documented decision on validation-only versus independent test reporting.
7. Any code fixes as a separate revision, with rerun results kept distinct from manuscript-reported numbers.

The split proportion is 20% validation in the code, but random initialization, shuffling, and augmentation are not seeded. Package versions are also not recorded. Exact reproduction cannot be promised from syntax validation alone.
