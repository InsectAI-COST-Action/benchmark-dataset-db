+++
# ── Identity ────────────────────────────────────────────────────────
title              = "InsectDCT"
description        = "Camera-trap images of insects on flowers and vegetation from nine European projects: about 61,000 for detection, and crops in 80 taxa for hierarchical classification."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Detection", "Classification"]
taxonomic_rank     = "mixed"
class_count        = 80
taxonomic_scope    = ["Odonata", "Dermaptera", "Orthoptera", "Hemiptera", "Hymenoptera",
                      "Coleoptera", "Diptera", "Lepidoptera", "Arachnida", "Diplopoda",
                      "Malacostraca"]
background         = ["complex"]
geographic_scope   = "Europe: Denmark, Germany, France, Malta, Netherlands, UK, Spain (Balearic Is.)"
composition        = "aggregated"
has_contextual_data = true
contextual_data    = ["trap-metadata"]
year               = 2026
license            = "CC-BY-4.0"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Kim Bjerge, Simon Wogram et al."
paper_url          = "https://doi.org/10.64898/2026.07.07.736939"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.5281/zenodo.21154490"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "zenodo-record"
provider     = "zenodo"
url          = "https://zenodo.org/records/21154490"
released     = 2026-07-03
note         = "The classification data, and the description of every file and folder."

[[assets]]
key          = "classifier-train"
provider     = "zenodo"
filename     = "classifierTrainV6.zip"
size_bytes   = 4641271446
url          = "https://zenodo.org/records/21154490/files/classifierTrainV6.zip?download=1"
note         = "Cropped insects in 80 taxa, one folder per taxon named <order> <family> <genus/species>."

[[assets]]
key          = "classifier-test"
provider     = "zenodo"
filename     = "classifierTestV6.zip"
size_bytes   = 207057891
url          = "https://zenodo.org/records/21154490/files/classifierTestV6.zip?download=1"
note         = "Classification test set, from camera locations not used in training."

[[assets]]
key          = "classifier-taxa-list"
provider     = "zenodo"
filename     = "classiferTrainV6.txt"
size_bytes   = 8659
url          = "https://zenodo.org/records/21154490/files/classiferTrainV6.txt?download=1"
note         = "The 80 taxa and image counts per level. The file name is spelled this way on Zenodo."

[[assets]]
key          = "detection-images"
provider     = "erda"
url          = "https://anon.erda.au.dk/cgi-sid/ls.py?share_id=AO4fCuU3fi"
note         = "Detection data in YOLO format: detectorColorYOLOV6.zip (51 GB), detectorMotionYOLOV6.zip (71 GB), detectorTestV6.zip (35 GB)."
+++

> Camera-trap images of insects on flowers and vegetation from nine European projects: about 61,000 for detection, and crops in 80 taxa for hierarchical classification.

**Intended use.** Benchmarking two stages of camera-trap insect monitoring on
cluttered, natural backgrounds: detecting arthropods in whole frames, and then
classifying the detected insects at three taxonomic levels. The classes focus
on the pollinators of northern and central Europe. It was assembled to train
the [InsectDCT pipeline](https://github.com/kimbjerge/insectDCT), which also
tracks insects over time.

## Contents

**Detection** (YOLO11 format, as RGB and as motion-enhanced images):

- **Training and validation:** 42,170 images with 36,758 annotated arthropods
  and other animals, from more than 30 plant families
- **Test:** 19,311 images, from new locations and plants, and from cameras of
  the same projects not used in training

**Classification** (cropped insects, labelled at three levels):

- **Classes:** 80 taxa at level 3, labelled `<order> <family> <genus or species>`,
  each as far down as could be identified. Bees, hoverflies and butterflies go to
  genus or species; other groups stop at family or order.
- **Taxa in the images:** eight insect orders (Odonata, Dermaptera, Orthoptera,
  Hemiptera, Hymenoptera, Coleoptera, Diptera, Lepidoptera), plus spiders,
  isopods and millipedes. The classifier also has classes for birds,
  herpetofauna, slugs, snails, insect larvae and vegetation, so that it can
  reject them; these are not arthropods and are not in the catalogue's scope.
- **Images:** 85,841 for training, with a 95% training and 5% validation split,
  plus a separate test set

## Sources

Compiled from several camera-trap projects, each with its own cameras and
plants: GreenRoof, GreenHouse, Arthropods, PollWatch, MAMBO, Orchard, Heather,
RT-Impact and ACS-HQ. The classification training data are supplemented with
images from GBIF of the species seen in the recordings.

## Contextual data

The project and camera are encoded in each file name (e.g. `MB_…` for MAMBO,
`PW_S?_…` for PollWatch); the Zenodo record lists every prefix. No separate
per-image table of dates or locations is included.

## Collection

Time-lapse and video recordings from camera traps pointed at flowers and
vegetation, mostly over single flowering seasons (May–September), with several
camera types: Wingscapes Pro, Logitech C922, Raspberry Pi cameras and others.
Images were resized to 1920×1080 for detection.

## Splits and benchmarks

Official splits for both tasks. The detection test set holds new locations and
plant families, including heather, to test how the detector generalises. The
preprint reports detection results for YOLO11 on RGB and motion-enhanced
images, and per-taxon F1 scores for the classifiers.

## Limitations

- **European pollinators.** The classifier's fine classes are northern and
  central European bees, hoverflies and butterflies; other insects are only
  labelled coarsely.
- **Uneven classes.** Bees make up about 29% of the classification training
  images; the smallest taxa have fewer than 100.
- **Mixed sources.** Camera types, resolutions and frame rates differ between
  projects, and the GBIF images differ in style from camera-trap crops.
- **Very large detection archives.** The detection data are 157 GB on ERDA, with
  no smaller subset.
- **Preprint.** The accompanying paper had not been peer reviewed when this
  entry was added.

## How to obtain the data

The classification data are on Zenodo; the detection data are on an Aarhus
University ERDA share, linked from the Zenodo record. No registration is
needed for either. Zenodo publishes MD5 checksums for its files.

The dataset is licensed CC BY 4.0, which permits commercial use with
attribution. The supplementary GBIF images were originally published under
the licenses of their GBIF records, so check those before reusing the GBIF
part on its own.

## Citation

```bibtex
@article{bjerge2026insectdct,
  title   = {{InsectDCT}: A generalised pipeline for detection, taxonomic classification, and tracking of insects in camera-trap recordings},
  author  = {Bjerge, Kim and Wogram, Simon and Serra-Marin, Pau Enric and H{\o}ye, Toke T.},
  journal = {bioRxiv},
  year    = {2026},
  doi     = {10.64898/2026.07.07.736939}
}

@dataset{bjerge2026insectdctdata,
  author    = {Bjerge, Kim and Wogram, Simon Friedrich Agathon and Serra-Marin, Pau Enric and Sakhelashvili, Otari and H{\o}ye, Toke T.},
  title     = {{InsectDCT}: Datasets for training and evaluating pipeline processing insect camera recordings},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.21154490}
}
```
