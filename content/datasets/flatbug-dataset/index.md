+++
# ── Identity ────────────────────────────────────────────────────────
title              = "flatbug-dataset"
description        = "6,028 images of terrestrial arthropods on flat surfaces, compiled from 23 published datasets and annotated with COCO instance polygons."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Detection", "Segmentation"]
taxonomic_rank     = "generic"
class_count        = 1
taxonomic_scope    = "Terrestrial arthropods, single generic class (no taxonomic labels)"
background         = ["simple"]
geographic_scope   = "Multi-region; depends on each source dataset"
composition        = "aggregated"
has_contextual_data = false
year               = 2025
license            = "CC-BY-4.0"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Quentin Geissmann, Asger Svenning"
paper_url          = "https://doi.org/10.1111/2041-210x.70249"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.5281/zenodo.14761447"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "zenodo-record"
provider     = "zenodo"
url          = "https://zenodo.org/records/14761447"
released     = 2025-01-29
note         = "The record page, with the per-dataset table and DOIs."

[[assets]]
key          = "images-and-annotations"
provider     = "zenodo"
filename     = "flatbug-dataset.zip"
size_bytes   = 6901887345
released     = 2025-01-29
url          = "https://zenodo.org/records/14761447/files/flatbug-dataset.zip?download=1"
note         = "All 23 datasets, one subdirectory each, with a COCO .json per subdirectory."
+++

> 6,028 images of terrestrial arthropods on flat surfaces, compiled from 23 published datasets and annotated with COCO instance polygons.

**Intended use.** Benchmarking models that detect and outline arthropods on
flat, uniform surfaces: sticky cards, pitfall- and light-trap imagery, scanners
and lab trays. It was assembled to train [flatbug](https://doi.org/10.1111/2041-210x.70249),
a generalist instance segmentation model, and covers many image sizes and
crowded scenes. It does not identify taxa: every instance is one class.

## Contents

- **Images:** 6,028
- **Annotations:** instance polygons in COCO format, one `.json` per source dataset
- **Classes:** one generic class, arthropod; no taxonomic labels
- **Tasks:** detection and instance segmentation

## Sources

A compilation of 23 independently published datasets, each stored in its own
subdirectory and each with its own DOI, listed in the archive's `metadata.csv`
and on the Zenodo record. They include ArTaxOr (1,050 images), PeMaToEuroPep
(729), amarathunga2022 (550), DiversityScanner (529), BIOSCAN (501), sticky-pi
(400), AMI-traps (153) and sittinger2023 (76).

## Contextual data

None at compilation level. Each source dataset has its own DOI and metadata;
see its record for what it provides.

## Collection

The images come from the 23 source datasets, so capture setups, cameras and
resolutions vary. All are on simple, uniform backgrounds: sticky cards, pitfall
and light traps, scanners, platforms and lab trays.

## Splits and benchmarks

Not stated at dataset level. The flatbug paper describes how the data were used
to train and evaluate the model; check it before comparing results.

## Limitations

- **No taxonomic labels.** Usable for finding and outlining arthropods, not for
  identifying them.
- **Simple backgrounds only.** No field imagery against vegetation or soil.
- **Uneven source sizes.** Sources range from 12 to 1,050 images, so a few
  datasets dominate.
- **Geography depends on the sources.** Regions vary between source datasets
  and are not recorded at compilation level.

## How to obtain the data

From Zenodo, as one 6.9 GB zip, no registration required. The DOI above is this
version of the record; 10.5281/zenodo.14761446 always resolves to the latest.
Zenodo publishes an MD5 checksum for the file,
`c10b7438f93eae8ba855babfa6bae751`, to check the download:
`md5 flatbug-dataset.zip` on macOS, `md5sum flatbug-dataset.zip` on Linux.

CC BY 4.0 permits commercial use with attribution. Cite the dataset and the
paper below, and consider citing the source datasets you use.

## Citation

```bibtex
@dataset{geissmann2025flatbugdataset,
  author    = {Geissmann, Quentin and Svenning, Asger},
  title     = {flatbug-dataset a compilation of dataset of terrestrial arthropodes on various surfaces},
  year      = {2025},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.14761447}
}

@article{svenning2026flatbug,
  title   = {A general method for detection and segmentation of terrestrial arthropods in images},
  author  = {Svenning, Asger and Mougeot, Guillaume and Alison, Jamie and Chevalier, Daphne
             and Molina, Nisa Chavez and Ong, Song-Quan and Bjerge, Kim and Carrillo, Juli
             and H{\o}ye, Toke Thomas and Geissmann, Quentin},
  journal = {Methods in Ecology and Evolution},
  volume  = {17},
  number  = {3},
  pages   = {727--739},
  year    = {2026},
  doi     = {10.1111/2041-210x.70249}
}
```
