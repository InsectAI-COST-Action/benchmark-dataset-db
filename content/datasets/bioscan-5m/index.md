+++
# ── Identity ────────────────────────────────────────────────────────
title              = "BIOSCAN-5M"
description        = "About 5.15 million microscope images of single arthropod specimens, labelled at seven taxonomic ranks, each with its DNA barcode, collection site and size."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification"]
taxonomic_rank     = "order"
class_count        = 55
taxonomic_scope    = ["Insecta", "Collembola", "Diplura", "Arachnida", "Chilopoda", "Diplopoda",
                      "Malacostraca", "Branchiopoda", "Copepoda", "Ostracoda"]
background         = ["simple"]
geographic_scope   = "Global: ~1,650 sites in 47 countries (>60% Costa Rica)"
composition        = "self-contained"
has_contextual_data = true
contextual_data    = ["genetic", "location", "morphological"]
year               = 2024
license            = "CC-BY-3.0"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Zahra Gharaee, Scott C. Lowe et al."
paper_url          = "https://doi.org/10.48550/arXiv.2406.12723"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.5281/zenodo.11973457"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "zenodo-record"
provider     = "zenodo"
url          = "https://zenodo.org/records/11973457"
released     = 2024-06-14
note         = "Version 1.0.0: cropped, resized images by partition, and the metadata."

[[assets]]
key          = "metadata"
provider     = "zenodo"
filename     = "BIOSCAN_5M_Insect_Dataset_metadata_MultiTypes.zip"
size_bytes   = 2065075527
url          = "https://zenodo.org/records/11973457/files/BIOSCAN_5M_Insect_Dataset_metadata_MultiTypes.zip?download=1"
note         = "Taxonomic labels, DNA barcodes, BINs, location, size and partition, one row per specimen."

[[assets]]
key          = "train"
provider     = "zenodo"
filename     = "BIOSCAN_5M_cropped_256_train.zip"
size_bytes   = 2224548648
url          = "https://zenodo.org/records/11973457/files/BIOSCAN_5M_cropped_256_train.zip?download=1"
note         = "Cropped images, 256 px on the shorter side: the labelled training partition."

[[assets]]
key          = "eval"
provider     = "zenodo"
filename     = "BIOSCAN_5M_cropped_256_eval.zip"
size_bytes   = 1467020347
url          = "https://zenodo.org/records/11973457/files/BIOSCAN_5M_cropped_256_eval.zip?download=1"
note         = "Cropped images, 256 px: the evaluation partitions."

[[assets]]
key          = "pretrain-part-1"
provider     = "zenodo"
filename     = "BIOSCAN_5M_cropped_256_pretrain.01.zip"
size_bytes   = 17914051002
url          = "https://zenodo.org/records/11973457/files/BIOSCAN_5M_cropped_256_pretrain.01.zip?download=1"
note         = "Cropped images, 256 px: the unlabelled-to-species pretraining partition, part 1 of 2."

[[assets]]
key          = "pretrain-part-2"
provider     = "zenodo"
filename     = "BIOSCAN_5M_cropped_256_pretrain.02.zip"
size_bytes   = 17702405477
url          = "https://zenodo.org/records/11973457/files/BIOSCAN_5M_cropped_256_pretrain.02.zip?download=1"
note         = "Part 2 of 2."

[[assets]]
key          = "full-size-images"
provider     = "google-drive"
url          = "https://drive.google.com/drive/u/1/folders/1Jc57eKkeiYrnUBc9WlIp-ZS_L1bVlT-0"
note         = "Full-resolution (1024×768) original and cropped images, and the other packages."
+++

> About 5.15 million microscope images of single arthropod specimens, labelled at seven taxonomic ranks, each with its DNA barcode, collection site and size.

**Intended use.** Benchmarking fine-grained and hierarchical classifiers of
arthropods, from order down to species, in both a closed-world setting
(identify species from a known list) and an open-world one (group specimens of
species never seen in training). Every record also has a DNA barcode, so it
suits image–DNA multimodal learning and clustering. It is a superset of
[BIOSCAN-1M](../bioscan-1m/). Each image shows one specimen, so it is not suited
to detection.

## Contents

- **Images:** 5,150,850, one specimen each, at 1024×768 px, as originals and as
  crops to the specimen
- **Labels:** seven ranks, as far down as each specimen was identified:

| Rank | Classes | Images labelled |
| --- | --- | --- |
| Phylum | 1 | 100% |
| Class | 10 | 99.9% |
| Order | 55 | 99.7% |
| Family | 934 | 95.8% |
| Subfamily | 1,542 | 28.6% |
| Genus | 7,605 | 23.8% |
| Species | 22,622 | 9.2% |
| Barcode Index Number (BIN) | 324,411 | 99.7% |

- **Taxa in the images:** arthropods of 10 classes, 98% of them insects. Insects
  span many orders, led by Diptera, Hymenoptera, Coleoptera, Hemiptera and
  Lepidoptera; the other classes are Arachnida, Collembola, Diplura, Chilopoda,
  Diplopoda and four crustacean classes (Malacostraca, Branchiopoda, Copepoda,
  Ostracoda). The catalogue lists insects as Insecta because the source does not
  publish a complete list of its insect orders.

The catalogue counts it as 55 orders, the finest rank almost every image is
labelled at. Many genus and species names are placeholders for undescribed
taxa (e.g. "*Oxysarcodexia* Malaise4749").

## Contextual data

For every specimen, in the metadata file:

- **Genetic:** the raw COI DNA barcode sequence and its Barcode Index Number (BIN)
- **Location:** country, province or state, and latitude–longitude of the
  collection site
- **Morphological:** specimen size

## Collection

Specimens were collected mainly with Malaise traps at about 1,650 sites in 47
countries, over 60% of them in Costa Rica, and each was photographed with a
Keyence VHX-7000 microscope, on a uniform background. The records
come from the BIOSCAN programme and were collected as one dataset.

## Splits and benchmarks

Official partitions come in the metadata. Species are first sorted into seen,
unseen, held-out and unknown sets, then records into partitions including
`pretrain` (not labelled to species), `train`, `val` and `test`, plus separate
partitions for unseen species used in the open-world tasks. The paper
benchmarks DNA-based classification, zero-shot clustering of image and DNA
embeddings, and image–DNA–text retrieval; results are reported in the source
publication.

## Limitations

- **Strongly long-tailed.** About 71% of specimens are Diptera; many
  taxa have only a handful of images.
- **Species labels are sparse.** Only 9.2% of images are labelled to species, and
  many of those names are placeholders.
- **Lab images only.** Single specimens under a microscope; a model trained here
  will not transfer directly to field or trap photographs.
- **Sampling bias.** Most specimens come from Costa Rica and from Malaise traps,
  which favour flying insects.

## How to obtain the data

From Zenodo (cropped, resized images by partition, and the metadata) or Google
Drive (full-size images and all packages). It is also on Hugging Face
(`Gharaee/BIOSCAN-5M`) and Kaggle, and a Python package, `bioscan-dataset`,
downloads and loads it. No registration is needed for Zenodo, which publishes
MD5 checksums for each file on the record page.

The images and metadata are licensed CC BY 3.0 by the Centre for Biodiversity
Genomics (CBG Photography Group), which permits commercial use with attribution.

## Citation

```bibtex
@inproceedings{gharaee2024bioscan5m,
  title     = {{BIOSCAN-5M}: A Multimodal Dataset for Insect Biodiversity},
  author    = {Gharaee, Zahra and Lowe, Scott C. and Gong, ZeMing and Millan Arias, Pablo
               and Pellegrino, Nicholas and Wang, Austin T. and Haurum, Joakim Bruslund
               and Zarubiieva, Iuliia and Kari, Lila and Steinke, Dirk and Taylor, Graham W.
               and Fieguth, Paul and Chang, Angel X.},
  booktitle = {Advances in Neural Information Processing Systems},
  volume    = {37},
  pages     = {36285--36313},
  year      = {2024}
}
```
