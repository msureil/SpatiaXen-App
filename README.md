# SpatiaXen

**An open-source interactive platform for cell-type-resolved spatial transcriptomics
analysis of 10x Genomics Xenium data.**

SpatiaXen works directly from raw transcript coordinates: it builds a kernel-density
gene-expression maps, infers cell types from marker genes, and quantifies
cell-type-specific expression, distance gradients, gene expression and density, and
cross-sample statistics over user-defined regions. It also offers a complement to
segmentation-based pipelines that generalise beyond any fixed experimental design.

Developed in the **Regenerative Engineering and Innovation Laboratory (REIL)**,
Michigan State University.

---

## ⬇️ Download & install

Get the latest installer from the **[Releases page](https://github.com/msureil/SpatiaXen-App/releases/latest)**.
No Python or setup required.

### macOS (Apple Silicon)
1. Download **[SpatiaXen.dmg](https://github.com/msureil/SpatiaXen-App/releases/latest/download/SpatiaXen.dmg)**.
2. Open it and drag **SpatiaXen** into **Applications**.
3. **First open (one time):** right-click **SpatiaXen** → **Open** → **Open**.
   - If macOS says it *"can't be verified"*: **System Settings → Privacy & Security → Open Anyway**.
   - If it says *"damaged"* (this just means unsigned), open **Terminal** and run:
     ```bash
     xattr -dr com.apple.quarantine /Applications/SpatiaXen.app
     ```
   Then open it normally.

### 🪟 Windows (64-bit)
1. Download **[SpatiaXen.exe](https://github.com/msureil/SpatiaXen-App/releases/latest/download/SpatiaXen.exe)**.
2. Double-click it. First launch takes ~10–30 s (it unpacks itself).
3. If **"Windows protected your PC"** appears: click **More info → Run anyway**
   (this only appears because the app isn't code-signed).

> Unsigned installers show a first-run security prompt — this is expected for free
> academic software and safe to allow.

---

## 🧪 Other ways to run it

**Python package (developers):**
```bash
pip install spatiaxen        # then run:  spatiaxen
# with GPU cell segmentation:  pip install spatiaxen[full]
```

**Server, browser-accessible (Docker):**
```bash
# CPU:
docker run -d -p 6080:6080 -v "$PWD/data:/data" anirban1231/spatiaxen:latest
# GPU:
docker run -d --gpus all -p 6080:6080 -v "$PWD/data:/data" anirban1231/spatiaxen:gpu
```
Then open **http://<server>:6080/vnc.html** (password `spatiaxen`).

**HPC cluster (Apptainer/Singularity):**
```bash
apptainer pull spatiaxen.sif docker://anirban1231/spatiaxen:gpu
apptainer run --nv --bind /path/to/data:/data spatiaxen.sif
```

---

## Using SpatiaXen
- On first launch, you accept the terms and register once (name, affiliation, email).
- Work left-to-right through the phases (Regions → Markers → Density → Nuclei →
  Cell Types → Expression → Statistics → Segmentation → Batch). Each tab has a
  **"ℹ How to use this tab"** button.
- **Cell segmentation (Phase 8)** needs PyTorch + Cellpose. The desktop app offers to
  **download & install them automatically** the first time you open Phase 8 (~2 GB,
  one time); the GPU Docker image and `pip install spatiaxen[full]` already include them.

## Requirements
- **Desktop:** macOS 11+ (Apple Silicon) or 64-bit Windows 10/11.
- Loading whole-slide Xenium files (tens of millions of transcripts) is comfortable
  with **32 GB RAM**; 64 GB is ideal.
- A GPU is only needed for Phase 8 segmentation (optional).

---

## 📄 Citation
If SpatiaXen contributes to your work, please cite:

> Thompson C, Chakraborty A, Wade-Kleyn L, Reimers M, Purcell E. *A systematic
> analysis of brain tissue response to microelectrode material and size with
> single-cell spatial transcriptomics.* bioRxiv (2026).
> [doi:10.64898/2026.03.12.711361](https://www.biorxiv.org/content/10.64898/2026.03.12.711361v1)

## Authors
- **Anirban Chakraborty** — Developer
- **Dr. Erin Purcell** and **Dr. Mark Reimers** — Project Coordinators

Michigan State University · [reil.iq.msu.edu](https://reil.iq.msu.edu) ·
contact: **chakra96@msu.edu**

## License
Released under the **MIT License**.
