+++
# ── Identity ────────────────────────────────────────────────────────
title              = "IP102"
description        = "75,222 web-sourced images of 102 crop insect pests in the wild, labelled by agricultural experts, with bounding boxes on about 19,000 of them."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification", "Detection"]
taxonomic_rank     = "mixed"
class_count        = 102
taxonomic_scope    = ["Orthoptera", "Thysanoptera", "Hemiptera", "Hymenoptera", "Coleoptera",
                      "Diptera", "Lepidoptera", "Arachnida"]
background         = ["complex"]
geographic_scope   = "Not stated"
composition        = "self-contained"
has_contextual_data = false
year               = 2019
license            = "Academic use only"
status             = "published"
date               = 2026-09-30

# Optional - delete a line to take the default shown.
developer          = "Xiaoping Wu, Chi Zhan, Yu-Kun Lai, Ming-Ming Cheng, Jufeng Yang"
paper_url          = "https://openaccess.thecvf.com/content_CVPR_2019/html/Wu_IP102_A_Large-Scale_Benchmark_Dataset_for_Insect_Pest_Recognition_CVPR_2019_paper.html"

# ── Data location ───────────────────────────────────────────────────
hosting_status     = "link_only"
commercial_use     = "permission_required"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "official-v1.1"
provider     = "google-drive"
url          = "https://drive.google.com/drive/folders/1svFSy2Da3cVMvekBwe13mzyx38XZ9xWo?usp=sharing"
note         = "The authors' IP102 v1.1, with the classification images and the detection subset. Also on AliyunDrive: https://www.aliyundrive.com/s/c5G9scSGyak"

[[assets]]
key          = "kaggle-classification"
provider     = "kaggle"
url          = "https://www.kaggle.com/datasets/rtlmhjbn/ip02-dataset"
note         = "Third-party Kaggle upload (Ratul Mahjabin) of the classification part only: 75.2k images, classes.txt and the train/val/test lists. 3.19 GB. Needs a Kaggle account to download."

[[assets]]
key          = "github"
provider     = "github"
url          = "https://github.com/xpwu95/IP102"
note         = "Project page: class list (classes.txt), pretrained models and the download links."
+++

> 75,222 web-sourced images of 102 crop insect pests in the wild, labelled by agricultural experts, with bounding boxes on about 19,000 of them.

**Intended use.** Benchmarking insect pest classification in field-like images:
fine-grained recognition across 102 pests of eight crops, on a long-tailed class
distribution, with each class spanning several life stages. A subset with
bounding boxes supports pest detection. It suits agricultural pest recognition
and imbalanced-learning research, not biodiversity monitoring: the classes are
chosen for crop damage, not taxonomic coverage.

## Contents

- **Images:** 75,222 for classification, JPEG, one pest category per image.
  Class sizes range from 71 to several thousand images (737 on average)
- **Detection subset:** 18,983 images with bounding boxes in Pascal VOC format
- **Classes:** 102 pest categories, most at species level but some broader, such
  as "aphids", "grub", "wireworm", "Thrips", "Miridae", "Limacodidae" and
  "Cicadellidae". The catalogue lists the rank as mixed for this reason
- **Taxa:** mainly Lepidoptera, Hemiptera, Coleoptera, Diptera, Thysanoptera,
  Orthoptera and Hymenoptera, plus several mites (Arachnida: Acari), such as
  "red spider", "longlegged spider mite" and "Panonchus citri"
- **Hierarchy:** each class has a super-class for the crop it mainly damages:
  rice (14 classes), corn (13), wheat (9), beet (8) and alfalfa (13) are field
  crops; vitis (16), citrus (19) and mango (10) are economic crops
- **Life stages:** a class can hold eggs, larvae, pupae and adults of the same pest

The full class list is in `classes.txt` on the GitHub page and in the Kaggle copy.

## Collection

Images were gathered from search engines (Google, Flickr, Bing and others) using
each pest's English name and synonyms, from agricultural and insect-science
websites, and from video frames captured at 5 fps: over 300,000 candidates.
Volunteers removed images with no pest or more than one pest category, and
duplicates, leaving about 120,000. Eight agricultural experts, one per crop, then
labelled them; an image was kept only if more than five experts agreed on its
class. Images are therefore varied in camera, resolution and setting, mostly
field or in-the-wild scenes rather than lab photographs.

## Splits and benchmarks

Official splits are published as image lists (`train.txt`, `val.txt`,
`test.txt`), split roughly 6:1:3 within each class.

- **Classification:** 45,095 train, 7,508 validation, 22,619 test
- **Detection:** 15,178 train, 3,798 test

Baselines reported in the source publication, on the test set:

| Model | Task | Metric | Value |
| --- | --- | --- | --- |
| ResNet-50 (ImageNet-pretrained, fine-tuned) | Classification | Accuracy | 49.4% |
| ResNet-50 (ImageNet-pretrained, fine-tuned) | Classification | F1 / G-mean | 40.1 / 31.5 |
| VGG-16 (fine-tuned) | Classification | Accuracy | 48.2% |
| FPN (ResNet-50) | Detection | AP / AP50 | 28.10 / 54.93 |
| YOLOv3 (DarkNet-53) | Detection | AP / AP50 | 25.67 / 50.64 |

Accuracy varies strongly by crop: 32.1% on rice pests versus 89.0% on mango
pests (ResNet-50, within each super-class).

## Limitations

- **Strongly imbalanced.** The imbalance ratio reaches 80.8 across the full
  dataset. Report per-class or balanced metrics, not accuracy alone.
- **Classes are not a consistent taxonomic rank.** Some are species, others
  genera, families or informal groups ("grub", "wireworm"), and a few class names
  are misspelled scientific names. Do not treat the labels as a species list.
- **Web-sourced images.** Collection location, date and camera are not recorded,
  and the geographic origin is not stated. The pest list leans towards crops and
  pests of East Asia.
- **Mixed life stages in one class.** Eggs, larvae, pupae and adults share a
  label, which makes some classes visually very diverse.
- **Possible label noise and near-duplicates.** Images came from search engines
  and video frames; the paper filtered duplicates, but frames from the same video
  may remain similar across splits.
- **Detection boxes cover only a quarter of the images**, and the Kaggle copy
  linked first here does not include them.

## How to obtain the data

The Kaggle copy is a third-party upload of the classification part only, with
the official split lists. It needs a (free) Kaggle account, and records its
license only as "Data files © Original Authors". For the detection annotations,
or the authors' own release (v1.1), use the Google Drive or AliyunDrive links on
the GitHub page. None of the links is pinned to a version or checksum.

There is no open license. The authors state that the dataset is free for
academic use, and that any other use needs permission from Xiaoping Wu
(xpwu95@163.com). Treat commercial use as not permitted without that permission.

## Citation

```bibtex
@inproceedings{wu2019ip102,
  title     = {{IP102}: A Large-Scale Benchmark Dataset for Insect Pest Recognition},
  author    = {Wu, Xiaoping and Zhan, Chi and Lai, Yu-Kun and Cheng, Ming-Ming and Yang, Jufeng},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages     = {8787--8796},
  year      = {2019}
}
```
