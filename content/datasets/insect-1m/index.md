+++
# ── Identity ────────────────────────────────────────────────────────
title              = "Insect-1M"
description        = "About one million naturalist images of arthropods, labelled by experts across a full taxonomic hierarchy down to 34,212 species, released as labels and image links."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification"]
taxonomic_rank     = "species"
class_count        = 34212
taxonomic_scope    = ["Insecta", "Collembola", "Protura", "Diplura", "Arachnida", "Merostomata",
                      "Pycnogonida", "Chilopoda", "Diplopoda", "Pauropoda", "Symphyla",
                      "Malacostraca", "Branchiopoda", "Ostracoda", "Maxillopoda"]
background         = ["complex"]
geographic_scope   = "Not stated"
composition        = "self-contained"
has_contextual_data = true
contextual_data    = ["other"]
year               = 2024
license            = "Not stated"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Hoang-Quan Nguyen, Thanh-Dat Truong et al. (CVIU Lab, University of Arkansas)"
paper_url          = "https://doi.org/10.48550/arXiv.2311.15206"

# ── Data location ───────────────────────────────────────────────────
hosting_status     = "link_only"
commercial_use     = "unknown"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "insect-1m-zip"
provider     = "github"
filename     = "Insect-1M.zip"
size_bytes   = 745892396
released     = 2026-07-04
url          = "https://github.com/uark-cviu/InsectFoundationModel/releases/download/v1/Insect-1M.zip"
note         = "GitHub release v1. Taxonomic labels and links to the source images, not the images themselves (per the paper). The release date is when this file was uploaded; the dataset dates from 2023."

[[assets]]
key          = "project-page"
provider     = "url"
url          = "https://uark-cviu.github.io/projects/insect-foundation"
note         = "Project page with the download link, dataset statistics, the Insect VQA benchmark and the Insect Foundation Model weights."
+++

> About one million naturalist images of arthropods, labelled by experts across a full taxonomic hierarchy down to 34,212 species, released as labels and image links.

**Intended use.** Pretraining insect and arthropod vision models, and
fine-grained or hierarchical classification at any rank from subphylum to
species. It was built to train the Insect Foundation Model, a self-supervised
ViT. It has no official splits or published results of its own, so it is a
training resource more than a ready-made benchmark: the paper evaluates its
model on IP102 instead.

## Contents

- **Images:** 1,017,036
- **Labels:** a dense taxonomic hierarchy for every image, with six main levels
  (subphylum, class, order, family, genus, species) and auxiliary levels such
  as suborder, superfamily, subfamily, tribe and subtribe:

| Rank | Classes |
| --- | --- |
| Subphylum | 4 |
| Class | 15 |
| Order | 91 |
| Family | 1,189 |
| Genus | 11,127 |
| Species | 34,212 |

- **Taxa:** Phylum Arthropoda, in four subphyla. Chelicerata: Arachnida,
  Merostomata, Pycnogonida. Crustacea: Branchiopoda, Malacostraca, Maxillopoda,
  Ostracoda. Hexapoda: Collembola, Diplura, Insecta, Protura. Myriapoda:
  Chilopoda, Diplopoda, Pauropoda, Symphyla. Insecta has the most images;
  Hymenoptera, Coleoptera and Lepidoptera are its largest orders
- **What is released:** labels and links to download each image, not the
  images. The authors say this is to preserve the rights of the image owners

The catalogue lists the scope as Insecta plus the 14 other classes; which
insect orders are present is not published beyond the largest ones.

## Contextual data

Text descriptions: for each taxon, the identification description crawled for
it, written from the higher levels (subphylum, class) down to the species.
These describe the taxon, not the individual image.

## Collection

The authors parsed over 1 million HTML pages of insect records "collected by
naturalists and entomologists", each with an image and its taxonomic label,
giving more than 2 million raw images. Entomology experts then removed
misidentified, corrupted and non-insect images, leaving 1,017,036. The source
website is not named in the paper or on the project page. Images are
photographs contributed by many people, so cameras, settings and backgrounds
vary.

## Splits and benchmarks

No official train/validation/test splits are published, and the paper reports
no results on Insect-1M itself. It is used only to pretrain the Insect
Foundation Model (ViT-B/16 and others), which is then fine-tuned and evaluated
on IP102; see that dataset's card.

The same project also released Insect VQA, a visual question answering
benchmark built from the IP102 test images, downloadable from the project page.

## Limitations

- **Not a benchmark as released.** No official splits and no reported
  baselines, so results on self-made splits are not comparable between papers.
- **Images must be fetched from their source.** Links can break over time, so
  the set you can rebuild may be smaller than the published one, and may differ
  from what the authors used.
- **Unknown source and rights.** The source website is not named, and no
  license is given for the labels or the images. Image copyright stays with the
  original photographers.
- **No geographic information.** Where the specimens were photographed is not
  stated or released.
- **Background not documented.** The images are naturalist photographs, so
  most are likely field shots; the paper does not describe them.
- **Imbalance at species level.** The paper reports orders as well balanced
  within the major classes but gives no per-species counts; with about 30
  images per species on average, many species will have very few.

## How to obtain the data

Download `Insect-1M.zip` (746 MB) from the GitHub release, linked from the
project page. No account is needed. The archive has not been inspected for this
entry: its contents are described here as the paper states them (labels and
image links), and there is no published checksum.

No license is stated on the project page, the GitHub repository or in the
paper, so reuse terms are unknown. Contact the authors before commercial use
or redistribution.

## Citation

```bibtex
@inproceedings{nguyen2024insect,
  title     = {Insect-Foundation: A Foundation Model and Large-scale {1M} Dataset for Visual Insect Understanding},
  author    = {Nguyen, Hoang-Quan and Truong, Thanh-Dat and Nguyen, Xuan Bac and Dowling, Ashley and Li, Xin and Luu, Khoa},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year      = {2024}
}
```
