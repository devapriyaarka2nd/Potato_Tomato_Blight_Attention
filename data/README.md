# Dataset layout

The supplied potato notebook explicitly selects these class folders under its dataset root:

- `PlantVillage/Potato___Early_blight/`
- `PlantVillage/Potato___Late_blight/`

The saved generator output records 1,600 training and 400 validation images. `validation_split=0.2` is used. No separate test directory or image-ID manifest is supplied. The last evaluation cell picks up to 150 files per class from the same dataset root, so that subset must not automatically be described as an independent test set.

A second evaluation cell expects `filtered_dataset/` but its filtering procedure, file list, and model identity are not provided. Confirm its class names and class order match the trained model.

The paper describes a tomato experiment too, but tomato code and data manifests were not uploaded. No tomato folder structure, implementation, or split manifest is fabricated in this package.

Add the verified PlantVillage source URL, export/version, permitted-use terms, and explicit image-ID split lists when available. The dataset itself is not redistributed. Keep images local and excluded from Git.
