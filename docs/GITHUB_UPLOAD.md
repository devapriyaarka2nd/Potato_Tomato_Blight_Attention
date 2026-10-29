# Upload this paper's project to GitHub

Suggested repository name: `Potato-Tomato-Blight-Attention-CNN`.

Suggested description: `Attention-based CNN research for potato and tomato blight classification; potato implementation currently included.`

Keep the potato and eventual tomato experiments in one repository because they support the same paper. Keep this separate from your retinal-vessel and other unrelated research repositories.

## Upload with the GitHub website

1. Extract `Potato-Tomato-Blight-Attention-CNN_Organized_Repository.zip`.
2. Create a repository for this paper, or open its existing repository if you already have one.
3. Upload the contents **inside** the extracted `Potato-Tomato-Blight-Attention-CNN` directory. `README.md` should be at the repository root, alongside `notebooks/`, `docs/`, `figures/`, `results/`, `data/`, `requirements.txt`, and `.gitignore`.
4. Include `.gitignore`, which can be hidden by a file browser. Website uploads are manual, so do not upload dataset directories or trained weights just because an ignore file exists.
5. Commit the files with a message such as `Organize potato attention CNN experiment and paper documentation`.
6. Open the README and notebook to verify the relative links, images, and folder placement.

If replacing an existing uploaded notebook, back up the original and confirm the new file is present before removing the old duplicate. The new notebook preserves all seven code cells but removes large saved outputs and adds explanatory sections. The original upload remains your historical reference.

The supplied notebook was about 87.5 MB, mostly because it embeds hundreds of image plots. The organized notebook is about 29 KB; selected figures and text outputs are stored separately. No prediction images were regenerated.

## Upload with Git instead

From the extracted project directory, initialize Git, add files, and commit. Then add the actual repository URL as the remote and push. Use your existing checkout/remote if the repository already exists; do not overwrite its history or initialize a competing repository unnecessarily.

No GitHub repository was created or modified during this package preparation.

## Complete the paper's code release later

- Add the original tomato notebook and map it in the README.
- Identify which trusted potato checkpoint generated each saved result.
- Add dataset split manifests, environment versions, and metric exports.
- Add a verified paper URL/DOI and final citation metadata.
- Choose a code license with the contributors.

Retain manuscript-reported values and verified rerun values as separate categories. Do not relabel the current snapshot as a verified reproduction until those checks have been completed.
