+++
# ── Identity ────────────────────────────────────────────────────────
title              = "Meta-Album Insects (SM_AM.INS)"
description        = "170,506 citizen-science photos of flower-visiting insects from France's SPIPOLL pollinator survey, resized to 128×128 and labelled in 117 mixed-rank categories."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification"]
taxonomic_rank     = "mixed"
class_count        = 117
taxonomic_scope    = ["Hemiptera", "Hymenoptera", "Coleoptera", "Diptera", "Lepidoptera", "Arachnida"]
background         = ["complex"]
geographic_scope   = "France"
composition        = "self-contained"
has_contextual_data = false
year               = 2022
license            = "CC-BY-NC-2.0"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Ihsan Ullah et al. (Meta-Album); original data by SPIPOLL, National Museum of Natural History, Paris"
paper_url          = "https://openreview.net/forum?id=70_Wx-dON3q"

# ── Data location ───────────────────────────────────────────────────
hosting_status     = "link_only"
commercial_use     = "prohibited"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "openml-extended"
provider     = "url"
variant      = "Extended (all 117 classes, 170,506 images)"
url          = "https://www.openml.org/d/44340"
note         = "OpenML dataset 44340. The label table (file name, category, super-category) is on OpenML; the images download alongside it through the OpenML Python API."

[[assets]]
key          = "openml-mini"
provider     = "url"
variant      = "Mini (104 classes, 40 images each)"
url          = "https://www.openml.org/d/44306"
note         = "OpenML dataset 44306. Class-balanced subset: every class with at least 40 images, sampled down to 40."

[[assets]]
key          = "openml-micro"
provider     = "url"
variant      = "Micro (20 classes, 40 images each)"
url          = "https://www.openml.org/d/44276"
note         = "OpenML dataset 44276. 20 randomly chosen classes from Mini."

[[assets]]
key          = "meta-album-page"
provider     = "url"
url          = "https://meta-album.github.io/datasets/INS.html"
note         = "Dataset page, with the info.json and datasheet."
+++

> 170,506 citizen-science photos of flower-visiting insects from France's SPIPOLL pollinator survey, resized to 128×128 and labelled in 117 mixed-rank categories.

**Intended use.** Benchmarking few-shot, meta-learning, transfer and continual
learning on a real-world, fine-grained insect domain. It is the insect dataset
of Meta-Album Set 2, a multi-domain meta-dataset, and was built for the NeurIPS
2022 Cross-Domain Meta-Learning competition. The Extended version also works as
an ordinary long-tailed classification set of European flower visitors. The
authors warn against using it for anything but machine-learning research and
benchmarks until its biases have been studied.

## Contents

- **Images:** 128×128 RGB, cropped square from the originals and resized with
  an anti-aliasing filter. Each shows one insect on a flower or vegetation
- **Versions:**

| Version | Classes | Images | Images per class |
| --- | --- | --- | --- |
| Extended | 117 | 170,506 | 22 to 49,555 (median 231) |
| Mini | 104 | 4,110 | 40 |
| Micro | 20 | 800 | 40 |

- **Labels:** a category and a super-category per image. Categories are the
  SPIPOLL identification groups, at different ranks: families (Apidae,
  Halictidae, Formicidae), genera (*Zygaena*, *Rhingia*, *Eristalis*) and single
  species (*Macroglossum stellatarum*, *Episyrphus balteatus*), plus
  informal groups such as "Les Syrphes difficiles à déterminer". Most category
  names are in French. Super-categories are superfamilies or families (29 in
  Extended)
- **Taxa:** bees and wasps (Apoidea alone is about 45% of the images),
  hoverflies and other flies, beetles, butterflies and moths, true bugs, and a
  few spiders (Araneidae)

## Collection

The original SPIPOLL data were created by the National Museum of Natural History
in Paris. Volunteers photograph insects on flowers, following a standard
protocol, and upload them with a proposed identification; each record is then
checked by other participants and experts, with three matching identifications
counting as valid. The source set has more than 290,000 images, collected
between May 2010 and April 2019, mostly in France. Meta-Album took a sample
covering all of its classes and preprocessed it; the original full-size images
are not part of this release but can be explored at spipoll.org.

## Splits and benchmarks

No fixed splits. Meta-Album generates train and test tasks on the fly, as
N-way k-shot episodes, so results depend on the sampling protocol. The Meta-Album
paper reports few-shot baselines across all its datasets; see it for the
protocol and the scores before comparing results. For standard classification
on the Extended version you must make your own split.

## Limitations

- **Very long-tailed (Extended).** One class has 49,555 images, the smallest
  22. The Mini and Micro versions are balanced, but small.
- **Labels are not one taxonomic rank.** Categories mix families, genera and
  species, and some are "hard to identify" groups, so it is not a species
  benchmark. Some French names have broken character encoding (e.g. "CharanÃ§ons").
- **Low resolution.** 128×128 images lose the fine detail often needed to tell
  similar species apart.
- **Only flower visitors in France.** Taxa and habitats are those of the SPIPOLL
  protocol; other regions, life stages and non-floral settings are not covered.
- **No contextual data.** SPIPOLL records location, date and plant, but this
  release has images and labels only.
- **Class counts differ between sources.** The website and OpenML say 117
  classes for Extended; the datasheet says 114.

## How to obtain the data

From OpenML, with no account needed. With the Python client:

```python
import openml
dataset = openml.datasets.get_dataset(44340, download_data=True, download_all_files=True)
```

Use 44306 for Mini and 44276 for Micro. OpenML publishes an MD5 checksum for
each version's label file.

The Meta-Album dataset page gives the license as CC BY-NC 2.0, the license of
the original SPIPOLL data. Note that the OpenML listing shows CC BY-NC 4.0,
Meta-Album's own license. Both are attribution, non-commercial licenses: cite
both the SPIPOLL paper and Meta-Album, and do not use it commercially.

## Citation

```bibtex
@inproceedings{meta-album-2022,
  title     = {Meta-Album: Multi-domain Meta-Dataset for Few-Shot Image Classification},
  author    = {Ullah, Ihsan and Carrion, Dustin and Escalera, Sergio and Guyon, Isabelle M and Huisman, Mike and Mohr, Felix and van Rijn, Jan N and Sun, Haozhe and Vanschoren, Joaquin and Vu, Phan Anh},
  booktitle = {Thirty-sixth Conference on Neural Information Processing Systems Datasets and Benchmarks Track},
  url       = {https://meta-album.github.io/},
  year      = {2022}
}

@article{serret2019spipoll,
  title   = {Data quality and participant engagement in citizen science: comparing two approaches for monitoring pollinators in France and South Korea},
  author  = {Serret, Hortense and Deguines, Nicolas and Jang, Yikweon and Lois, Gregoire and Julliard, Romain},
  journal = {Citizen Science: Theory and Practice},
  volume  = {4},
  number  = {1},
  pages   = {22},
  year    = {2019}
}
```
