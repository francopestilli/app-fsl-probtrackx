# app-fsl-probtrackx

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Runs FSL probtrackx2 (GPU) surface-seeded probabilistic tractography from BedpostX samples, with avoid, target and termination masks, for one hemisphere.**

Wraps probtrackx2_gpu with fixed settings (50000 samples, 3200 steps, 0.3125 mm step, loop check, modified Euler, caret mesh space) and outputs streamline density and seed-to-target counts. Seeds come from a GIFTI surface for the chosen hemisphere, with the FA map as seed reference. Used for surface-based tractography of prefrontal pathways (Bedini et al., 2026). Needs BedpostX output and all masks in diffusion space.

| | |
|---|---|
| 📥 **Inputs** | `neuro/FSLBedpostX` · `neuro/mask` ×2 · `neuro/surface/data` ×3 · `neuro/tensor` |
| 📤 **Outputs** | `raw` |
| 🐳 **Container** | `brainlife/fsl:6.0.1` |
| ⚙️ **Resources** | 2 CPUs · 3.5 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.863](https://doi.org/10.25663/brainlife.app.863) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `bedpostx` | `neuro/FSLBedpostX` | yes | FSL BedpostX output (merged samples). |
| `brain_mask` | `neuro/mask` | yes | Brain mask in diffusion space. |
| `seed_surface` | `neuro/surface/data` | yes | Seed surfaces (GIFTI) for the left and right hemispheres. |
| `seed_reference` | `neuro/tensor` | yes | Tensor maps; FA is used as the seed reference image. |
| `mask_avoid` | `neuro/mask` | yes | Exclusion (avoid) mask. |
| `mask_target` | `neuro/surface/data` | yes | Target masks list for seed-to-target counts. |
| `mask_termination` | `neuro/surface/data` | yes | Termination surfaces (e.g. pial) for each hemisphere. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `probtrackx_outputs` | `raw` | probtrackx2 output directory (fdt_paths, waytotal and seed-to-target counts). |

<details>
<summary><b>⚙️ Parameters</b> (1)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `hemisphere` | enum |  | Hemisphere to track (selects the left or right seed and termination files). Options: `1`, `2`. |

</details>

📚 **References used by this App:**
- Bedini M, Olivetti E, Avesani P, Baldauf D. Surface-based Tractography uncovers 'What' and 'Where' Pathways in Prefrontal Cortex. Cortex (2026). [doi:10.1016/j.cortex.2026.03.016](https://doi.org/10.1016/j.cortex.2026.03.016)
- Behrens TEJ, Berg HJ, Jbabdi S, Rushworth MFS, Woolrich MW. Probabilistic diffusion tractography with multiple fibre orientations: What can we gain? NeuroImage 34(1):144-155 (2007). [doi:10.1016/j.neuroimage.2006.09.018](https://doi.org/10.1016/j.neuroimage.2006.09.018)
- Hayashi S, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. Nat Methods (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)

<!-- brainlife-app:end -->

If you use this script for your research, please cite:
1. Bedini, M., Olivetti, E., Avesani, P., & Baldauf, D. (2026). Surface-based Tractography uncovers ‘What’ and ‘Where’ Pathways in Prefrontal Cortex. Cortex. https://doi.org/10.1016/j.cortex.2026.03.016
2. Behrens, T. E. J., Berg, H. J., Jbabdi, S., Rushworth, M. F. S., & Woolrich, M. W. (2007). Probabilistic diffusion tractography with multiple fibre orientations: What can we gain? NeuroImage, 34(1), 144–155. https://doi.org/10.1016/j.neuroimage.2006.09.018
3. Hayashi, S., Caron, B. A., Heinsfeld, A. S., Vinci-Booher, S., McPherson, B., Bullock, D. N., Bertò, G., Niso, G., Hanekamp, S., Levitas, D., Ray, K., MacKenzie, A., Kitchell, L., Leong, J. K., Nascimento-Silva, F., Koudoro, S., Willis, H., Jolly, J. K., Pisner, D., … Pestilli, F. (2023). brainlife.io: A decentralized and open source cloud platform to support neuroscience research. https://doi.org/10.1038/s41592-024-02237-2
