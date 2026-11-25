<h1 align="center">DBB_DiceScore</h1>

<p align="center">
  Computes the Dice similarity coefficient (DSC) between two segmentations (parcellations)
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.579"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.579-blue.svg" alt="Run on brainlife.io"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes the Dice similarity coefficient (DSC) between two segmentations (parcellations)**

Compares a computed segmentation with a ground-truth segmentation label by label and writes the Dice similarity coefficient of each label, sorted by label value, to a text file. Use it to evaluate tissue segmentation methods, for example on the DBB Distorted Brain Benchmark. Both volumes must be on the same voxel grid and use the same label values.

| | |
|---|---|
| **Inputs** | `neuro/parcellation/volume` ×2 |
| **Outputs** | `raw` |
| **Container** | `gamorosino/bl_app_dbb_disseg` |
| **Resources** | 1 CPUs · 0.25 h walltime |
| **Run it** | [doi.org/10.25663/brainlife.app.579](https://doi.org/10.25663/brainlife.app.579) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `computed` | `neuro/parcellation/volume` | yes | Segmentation (parcellation volume) produced by the method under evaluation. Same voxel grid and label values as the ground truth. |
| `groud_truth` | `neuro/parcellation/volume` | yes | Reference (ground-truth) segmentation volume. Same voxel grid and label values as the computed segmentation. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `dice_score` | `raw` | dice_score.txt with the Dice score of each label, space-separated and sorted by label value. |

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.579](https://doi.org/10.25663/brainlife.app.579), choose `neuro/parcellation/volume`, `neuro/parcellation/volume` from your project and press **Execute**. The results are saved to your project as `raw`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `gamorosino/bl_app_dbb_disseg`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "computed": "/path/to/computed/computed",
       "groud_truth": "/path/to/groud_truth/groud_truth"
   }
   ```

3. Run `./main`.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- DBB_DiceScore. brainlife.io App. [doi:10.25663/brainlife.app.579](https://doi.org/10.25663/brainlife.app.579)
- Amorosino G, Peruzzo D, Redaelli D, Olivetti E, Arrigoni F, Avesani P. DBB - A Distorted Brain Benchmark for Automatic Tissue Segmentation in Paediatric Patients. NeuroImage 119486 (2022). [doi:10.1016/j.neuroimage.2022.119486](https://doi.org/10.1016/j.neuroimage.2022.119486)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

Gabriele Amorosino
