+++
# ── Identity ────────────────────────────────────────────────────────
title              = "Mothbox Training Dataset 1.1"
description        = "1,695 high-resolution images of nocturnal insects at Mothbox light attractors in 14 countries, with 14,549 oriented bounding boxes around every animal on the sheet."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Detection"]
taxonomic_rank     = "generic"
class_count        = 1
taxonomic_scope    = ["Insecta"]
background         = ["simple"]
geographic_scope   = "14 countries: Panama, Ecuador, Peru, Argentina, USA, Canada, Ireland, Poland, Netherlands, Germany, Denmark, Italy, Croatia, Indonesia"
composition        = "self-contained"
has_contextual_data = true
contextual_data    = ["collection-date", "time-of-day", "trap-metadata"]
year               = 2026
license            = "CC-BY-4.0"
status             = "published"
date               = 2026-10-09

# Optional - delete a line to take the default shown.
developer          = "Kit Quitmeyer, Andrew Quitmeyer (Digital Naturalism Laboratories)"
paper_url          = "https://mothbox.org/"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.5281/zenodo.23140320"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "zenodo-record"
provider     = "zenodo"
url          = "https://zenodo.org/records/23140320"
released     = 2026-10-04
note         = "The record page, with the dataset statistics, the collectors per country and MD5 checksums."

[[assets]]
key          = "train-part-1"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_train_part01of05.zip"
size_bytes   = 4280570066
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_train_part01of05.zip?download=1"
note         = "Training split, part 1 of 5. Each part is a standalone zip of images/train and labels/train."

[[assets]]
key          = "train-part-2"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_train_part02of05.zip"
size_bytes   = 4289757946
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_train_part02of05.zip?download=1"

[[assets]]
key          = "train-part-3"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_train_part03of05.zip"
size_bytes   = 4293230671
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_train_part03of05.zip?download=1"

[[assets]]
key          = "train-part-4"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_train_part04of05.zip"
size_bytes   = 4291670274
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_train_part04of05.zip?download=1"

[[assets]]
key          = "train-part-5"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_train_part05of05.zip"
size_bytes   = 3870035067
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_train_part05of05.zip?download=1"

[[assets]]
key          = "val"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_val.zip"
size_bytes   = 2594516640
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_val.zip?download=1"
note         = "Validation split: 169 images, 939 boxes."

[[assets]]
key          = "test"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_test.zip"
size_bytes   = 2600763902
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_test.zip?download=1"
note         = "Test split: 170 images, 1,694 boxes."

[[assets]]
key          = "patches"
provider     = "zenodo"
filename     = "Mothbox_Training_Dataset_1-1_patches.zip"
size_bytes   = 190457473
released     = 2026-10-04
url          = "https://zenodo.org/records/23140320/files/Mothbox_Training_Dataset_1-1_patches.zip?download=1"
note         = "14,544 crops, one per annotated animal, named after their source image. Not tiles: no empty background."
+++

> 1,695 high-resolution images of nocturnal insects at Mothbox light attractors in 14 countries, with 14,549 oriented bounding boxes around every animal on the sheet.

**Intended use.** Training and benchmarking detectors that find every animal on
the illuminated sheet of an automated light trap, from large moths down to tiny,
motion-blurred flies. It was annotated to train the Mothbox's own detector, and
its images come from many Mothbox builds deployed in the tropics as well as in
Europe and North America. It does not identify taxa: every box is one class.

## Contents

- **Images:** 1,695 full-resolution JPEGs, about 26 GB. 1,187 are 9248 × 6944
  px (64 MP) and 508 are 9000 × 6000 px (54 MP).
- **Annotations:** 14,549 **oriented** bounding boxes in YOLO OBB format, one
  `.txt` per image (`class x1 y1 x2 y2 x3 y3 x4 y4`, normalised), drawn in
  X-AnyLabeling. A `data.yaml` names the class and the splits.
- **Classes:** one, `creature`: anything the annotators were sure was an animal
  (vs. background, dirt, frass or plants), including very small and blurred
  ones. Almost all are insects; the scope is listed as Insecta, but other
  arthropods on the sheet may also be boxed.
- **Background images:** 302 images with no animals at all, included on purpose
  to cut false positives on empty sheets, debris and glare.
- **Density:** 8.6 boxes per image on average, median 2, maximum 1,781.
- **Box size** (square root of box area): median about 111 px; the middle 90%
  is 41 to 552 px; the full range is 14 to 2,964 px.

The record also holds the patches archive listed above, and `MBD-1-1`, a
YOLO26s OBB detector trained on this data (`.pt` and `.onnx`, with its
config).

## Contextual data

No per-image table. Most file names hold the Mothbox's name and the capture
date and time, e.g. `adeptTurca_2024_09_02__02_40_18_HDR0.jpg`; a few dozen use
other patterns (a collector's name and an ISO timestamp, for example). From the
file names, the images come from about 50 Mothboxes between 2024 and 2026.
Countries and collectors are listed only at dataset level, on the Zenodo record.

## Collection

Images were taken at night by Mothboxes, open-source automated light traps,
of various models and community remixes, photographing an illuminated sheet.
They were deployed in 14 countries between 2024 and 2026 by about 20 collectors,
with Panama, Indonesia, Ecuador, Peru, Argentina, the USA, Canada and several
European countries among them.

## Splits and benchmarks

Official train, validation and test splits, set in `data.yaml`:

| Split | Images | Boxes | Background images |
| --- | ---: | ---: | ---: |
| train | 1,356 | 11,916 | 256 |
| val | 169 | 939 | 21 |
| test | 170 | 1,694 | 25 |

The splits are drawn from the same deployments. Every Mothbox in the
validation and test splits also appears in training, and about nine in ten of
their images come from a device and night that also appear in training. Scores
on the official test split therefore measure performance on known sites and
devices. To measure generalisation to new sites, re-split by Mothbox or by
country.

No benchmark scores are reported with the dataset. The included `MBD-1-1`
model is a starting point, not a published baseline.

## Limitations

- **No taxonomic labels.** Usable for finding animals, not for identifying them.
- **Oriented boxes.** Tools that expect axis-aligned boxes need them converted
  (the min and max of the four corners), which loosens the box around insects
  lying diagonally.
- **Splits share deployments.** See above: the test split is not independent of
  training by site, device or night.
- **Small objects in huge frames.** A median box of about 111 px in a 9248 px
  wide image means training or inference at standard detector input sizes
  without tiling loses most of the smaller insects.
- **Uneven density.** Most images hold a few animals; a handful hold hundreds,
  one of them 1,781.
- **Light sheets only.** Nocturnal insects on a white sheet: no day-flying
  insects, no natural backgrounds. Lighting, sheet and camera differ between
  Mothbox models.
- **No paper.** The statistics here are the ones the Zenodo record states, apart
  from the deployment overlap, which was worked out from the file names.

## How to obtain the data

From Zenodo, no registration required: seven zips totalling about 26 GB (the
training split in five standalone parts, plus validation and test), and the
optional patches archive. Extract them all into one folder to get the
`images/` and `labels/` layout that `data.yaml` expects. Zenodo publishes an MD5
checksum for every file.

The DOI above is version 1.1; 10.5281/zenodo.23140319 always resolves to the
latest version. CC BY 4.0 permits commercial use with attribution.

## Citation

```bibtex
@dataset{quitmeyer2026mothbox,
  author    = {Quitmeyer, Kit and Quitmeyer, Andrew},
  title     = {Mothbox Training Dataset 1-1},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.23140320}
}
```
