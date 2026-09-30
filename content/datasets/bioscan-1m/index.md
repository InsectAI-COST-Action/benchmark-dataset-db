+++
# ── Identity ────────────────────────────────────────────────────────
title              = "BIOSCAN-1M"
description        = "About 1.1 million microscope images of single insect specimens, labelled by experts at several taxonomic ranks, each with its DNA barcode."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification"]
taxonomic_rank     = "order"
class_count        = 16
taxonomic_scope    = "Insecta; every image to order, 98.6% to family (491), 22.5% to genus (3,441), 7.5% to species (8,355). Long-tailed, Diptera-dominated"
background         = ["simple"]
geographic_scope   = "3 countries: Costa Rica, Canada, South Africa (mostly Costa Rica)"
composition        = "self-contained"
has_contextual_data = true
contextual_data    = ["genetic"]
year               = 2023
license            = "CC-BY-3.0"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Zahra Gharaee, ZeMing Gong et al."
paper_url          = "https://doi.org/10.48550/arXiv.2307.10455"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.5281/zenodo.8030065"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "zenodo-record"
provider     = "zenodo"
url          = "https://zenodo.org/records/8030065"
released     = 2023-06-12
note         = "Version 1.0.0: resized images and the metadata file."

[[assets]]
key          = "cropped-256"
provider     = "zenodo"
filename     = "cropped_256.zip"
size_bytes   = 7171212982
url          = "https://zenodo.org/records/8030065/files/cropped_256.zip?download=1"
note         = "Images cropped to the specimen, resized to 256 px on the shorter side. Also as cropped_256.hdf5."

[[assets]]
key          = "original-256"
provider     = "zenodo"
filename     = "original_256.zip"
size_bytes   = 26364230180
url          = "https://zenodo.org/records/8030065/files/original_256.zip?download=1"
note         = "Uncropped images, resized to 256 px on the shorter side."

[[assets]]
key          = "metadata"
provider     = "zenodo"
filename     = "BIOSCAN_Insect_Dataset_metadata.tsv"
size_bytes   = 1227580325
url          = "https://zenodo.org/records/8030065/files/BIOSCAN_Insect_Dataset_metadata.tsv?download=1"
note         = "Taxonomic labels, DNA barcodes, BINs and the paper's train/validation/test splits, one row per image. Also as .jsonld."

[[assets]]
key          = "full-size-images"
provider     = "google-drive"
url          = "https://drive.google.com/drive/u/1/folders/1kD9cXuQ1FdL30etp7sjy_Gs_NAAJ3EXI"
note         = "Full-resolution original and cropped images, 113 zip files each."
+++

> About 1.1 million microscope images of single insect specimens, labelled by experts at several taxonomic ranks, each with its DNA barcode.

**Intended use.** Benchmarking fine-grained and hierarchical insect classifiers:
from order down to species, on a long-tailed distribution where a few groups
dominate. Every image comes with its specimen's DNA barcode, so it also suits
work linking images to genetic identities. Each image shows one specimen, so it
is not suited to detection.

## Contents

- **Images:** 1,128,313, as originals and as crops to the specimen
- **Labels:** expert taxonomic labels, as far down as each specimen was identified:

| Rank | Classes | Images labelled |
| --- | --- | --- |
| Order | 16 | 100% |
| Family | 491 | 98.6% |
| Subfamily | 760 | 23.5% |
| Tribe | 535 | 5.4% |
| Genus | 3,441 | 22.5% |
| Species | 8,355 | 7.5% |
| Barcode Index Number (BIN) | 90,918 | 100% |

The catalogue lists it as 16 orders, the rank every image is labelled at. The
deeper ranks are there for the images that were identified further.

## Contextual data

Genetic, for every specimen: the raw COI DNA barcode sequence and its Barcode
Index Number (BIN), a genetically based proxy for species. Both are in the
metadata file.

## Collection

Specimens were collected with Malaise traps, mostly in Costa Rica, Canada and
South Africa, and each was photographed in a plate well with a Keyence VHX-7000
microscope, on a uniform background. It is a subset of the BIOSCAN programme,
collected as one dataset.

## Splits and benchmarks

The metadata file marks which images were used for training, validation and
testing in each of the paper's six experiments. The paper's baseline tasks
classify images into the 16 orders, and Diptera images into 40 families.
Results are reported in the source publication.

## Limitations

- **Strongly long-tailed.** Diptera dominate; many families, genera and species
  have very few images.
- **Species labels are sparse.** Only 7.5% of images are identified to species,
  so species-level benchmarks use a small, uneven subset.
- **Lab images only.** Single specimens under a microscope; a model trained here
  will not transfer directly to field or trap photographs.
- **Three countries.** Neotropical, Nearctic and Afrotropical fauna only; other regions are not covered.

## How to obtain the data

From Zenodo (resized images and metadata) or Google Drive (full-size images). The
dataset is also mirrored on Kaggle and Hugging Face (`Gharaee/BIOSCAN_1M_Insect_Dataset`).
No registration is needed for Zenodo. Zenodo publishes MD5 checksums for each
file on the record page.

The images are licensed CC BY 3.0 by the Centre for Biodiversity Genomics (CBG
Photography Group), which permits commercial use with attribution. The project's
code on GitHub is separately MIT-licensed.

## Citation

```bibtex
@inproceedings{gharaee2023step,
  author    = {Gharaee, Z. and Gong, Z. and Pellegrino, N. and Zarubiieva, I. and Haurum, J. B. and Lowe, S. C. and McKeown, J. T. A. and Ho, C. Y. and McLeod, J. and Wei, Y. C. and Agda, J. and Ratnasingham, S. and Steinke, D. and Chang, A. X. and Taylor, G. W. and Fieguth, P.},
  title     = {A Step Towards Worldwide Biodiversity Assessment: The {BIOSCAN-1M} Insect Dataset},
  booktitle = {Advances in Neural Information Processing Systems ({NeurIPS}) Datasets \& Benchmarks Track},
  year      = {2023}
}
```
