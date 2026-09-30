+++
# ── Identity ────────────────────────────────────────────────────────
title              = "iNat2021"
description        = "About 700,000 iNaturalist field photos of 2,679 insect and arachnid species, the arthropod part of a 10,000-species tree-of-life dataset that must be subset before use."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification"]
taxonomic_rank     = "species"
class_count        = 2679
taxonomic_scope    = ["Insecta", "Arachnida"]
needs_subsetting   = true
background         = ["complex"]
geographic_scope   = "Global"
composition        = "self-contained"
has_contextual_data = true
contextual_data    = ["location", "collection-date"]
year               = 2021
license            = "Custom: non-commercial research and education"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Grant Van Horn, Elijah Cole, Sara Beery, Kimberly Wilber, Serge Belongie, Oisin Mac Aodha (Visipedia)"
paper_url          = "https://doi.org/10.48550/arXiv.2103.16483"

# ── Data location ───────────────────────────────────────────────────
hosting_status     = "link_only"
commercial_use     = "prohibited"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "competition-page"
provider     = "github"
url          = "https://github.com/visipedia/inat_comp/tree/master/2021"
note         = "Dataset description, annotation format, terms of use, and the download links and MD5 checksums below."

[[assets]]
key          = "train-mini-annotations"
provider     = "url"
filename     = "train_mini.json.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/train_mini.json.tar.gz"
note         = "45 MB. COCO-style JSON with the full taxonomy (kingdom to species) per category: filter on class Insecta to find the insect subset. md5 395a35be3651d86dc3b0d365b8ea5f92"

[[assets]]
key          = "train-mini-images"
provider     = "url"
filename     = "train_mini.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/train_mini.tar.gz"
note         = "42 GB. 50 images per species (500,000 in total), one folder per species. md5 db6ed8330e634445efc8fec83ae81442"

[[assets]]
key          = "train-annotations"
provider     = "url"
filename     = "train.json.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/train.json.tar.gz"
note         = "221 MB. md5 38a7bb733f7a09214d44293460ec0021"

[[assets]]
key          = "train-images"
provider     = "url"
filename     = "train.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/train.tar.gz"
note         = "224 GB, all 2,686,843 training images. One archive: you must download all of it to extract the insects. md5 e0526d53c7f7b2e3167b2b43bb2690ed"

[[assets]]
key          = "val-annotations"
provider     = "url"
filename     = "val.json.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/val.json.tar.gz"
note         = "9.4 MB. md5 4d761e0f6a86cc63e8f7afc91f6a8f0b"

[[assets]]
key          = "val-images"
provider     = "url"
filename     = "val.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/val.tar.gz"
note         = "8.4 GB, 10 images per species (100,000). md5 f6f6e0e242e3d4c9569ba56400938afc"

[[assets]]
key          = "test-images"
provider     = "url"
filename     = "public_test.tar.gz"
url          = "https://ml-inat-competition-datasets.s3.amazonaws.com/2021/public_test.tar.gz"
note         = "43 GB, 500,000 images with no public labels (scored only on the closed Kaggle competition). Test info: public_test.json.tar.gz. md5 7124b949fe79bfa7f7019a15ef3dbd06"
+++

> About 700,000 iNaturalist field photos of 2,679 insect and arachnid species, the arthropod part of a 10,000-species tree-of-life dataset that must be subset before use.

**Intended use.** Large-scale, fine-grained species classification of
arthropods from citizen-science field photographs, with location and date for
every image. This entry describes only the arthropod part of iNat2021: the
insects and arachnids. The dataset itself covers 10,000 species across the tree
of life, so you must extract this subset yourself before benchmarking (see
Subsetting below). It is one of the largest open sets of field photos of
insects identified to species.

## Contents

The arthropod subset, as defined by iNat2021's supercategories:

| Supercategory | Species | Train | Train mini | Val |
| --- | --- | --- | --- | --- |
| Insects | 2,526 | 663,682 | 126,300 | 25,260 |
| Arachnids | 153 | 40,687 | 7,650 | 1,530 |
| **Arthropod total** | **2,679** | **704,369** | **133,950** | **26,790** |

- **Labels:** one species per image, with its full taxonomy (kingdom, phylum,
  class, order, family, genus, specific epithet), common name and supercategory
- **Images:** longest side at most 500 px, JPEG. Train-mini has 50 images per
  species and validation 10 per species. The test set's labels are not public
- **Annotations:** COCO-style JSON, one label per image

The class count above (2,679) and the taxonomic scope cover these two groups
only. The "Animalia" supercategory (142 species of other animals) may also hold
some arthropods, such as centipedes, millipedes or crustaceans; they are not
counted here.

For context, the full dataset (10,000 species, 2,686,843 train, 500,000
train-mini, 100,000 validation and 500,000 test images) is made up of:

| Supercategory | Species | Train | Train mini | Val |
| --- | --- | --- | --- | --- |
| Insects | 2,526 | 663,682 | 126,300 | 25,260 |
| Arachnids | 153 | 40,687 | 7,650 | 1,530 |
| Plants | 4,271 | 1,148,702 | 213,550 | 42,710 |
| Birds | 1,486 | 414,847 | 74,300 | 14,860 |
| Fungi | 341 | 90,048 | 17,050 | 3,410 |
| Reptiles | 313 | 86,830 | 15,650 | 3,130 |
| Mammals | 246 | 68,917 | 12,300 | 2,460 |
| Ray-finned fishes | 183 | 45,166 | 9,150 | 1,830 |
| Amphibians | 170 | 46,252 | 8,500 | 1,700 |
| Mollusks | 169 | 44,670 | 8,450 | 1,690 |
| Animalia (other) | 142 | 37,042 | 7,100 | 1,420 |

**Subsetting.** Filter the `categories` in the annotation JSON on
`class == "Insecta"` (or `supercategory == "Insects"`), keep the images whose
annotations point at those categories, and copy only their folders out of the
extracted archive (`train/<image_dir_name>/`). Add `class == "Arachnida"` for
spiders, mites and relatives. To catch any other arthropods, filter on
`phylum == "Arthropoda"` instead and check which classes appear. Which insect
orders are present is in the `order` field but is not summarised by the
authors.

## Contextual data

Per image: latitude, longitude, location uncertainty (metres) and observation
date. Location is `null` where the observation's location is private or the
species is sensitive, and location uncertainty contains raw, sometimes bogus
values (e.g. `-80`). Each image also records its own license and rights holder.

## Collection

Images come from research-grade observations on iNaturalist, the citizen-science
platform, uploaded by the public and identified by the community. They are
mostly photos of living organisms in the field, taken with phones and cameras,
worldwide but with most observations from North America and Europe. The dataset
was built for the iNat 2021 competition at the FGVC8 workshop (CVPR 2021).

## Splits and benchmarks

Official splits: train (or train-mini), validation and test. Test labels are not
public; the test set was scored top-1 on the [Kaggle
competition](https://www.kaggle.com/c/inaturalist-2021). In practice, results on
iNat2021 are reported on the validation set. Published results are for all
10,000 species; there is no official insect-only split, so results on an insect
subset are not comparable to them, or to each other unless the subset is the same.

## Limitations

- **Mostly not arthropods.** Insects and arachnids are about 27% of the species
  and 26% of the training images. The subset must be made before benchmarking,
  and the authors do not define one.
- **Huge downloads for a subset.** The full training set is one 224 GB archive,
  so getting the insect images means downloading everything. Train-mini (42 GB)
  is a lighter option.
- **Geographic bias.** Observations are concentrated in North America and
  Europe, following where iNaturalist users are.
- **Photo bias.** Mostly large, conspicuous, adult insects photographed by the
  public; small, cryptic and immature insects are under-represented.
- **Label noise.** Community identifications can be wrong, and some species
  are hard to tell apart from photos.
- **Not trap or lab imagery.** A model trained here may not transfer to light
  traps, sticky traps or specimen photographs.

## How to obtain the data

Download from the AWS Open Data bucket listed on the competition page (links
above), with no account needed. MD5 checksums are given for every file.

There is no standard license for the dataset as a whole. By downloading it you
agree to its terms of use: follow the iNaturalist Terms of Service, use it only
for non-commercial research and education, and do not redistribute the images.
Each image also carries its own license (given in the annotation file) and
rights holder.

## Citation

```bibtex
@inproceedings{vanhorn2021benchmarking,
  title     = {Benchmarking Representation Learning for Natural World Image Collections},
  author    = {Van Horn, Grant and Cole, Elijah and Beery, Sara and Wilber, Kimberly and Belongie, Serge and Mac Aodha, Oisin},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year      = {2021}
}
```
