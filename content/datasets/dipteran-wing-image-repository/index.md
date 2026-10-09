+++
# ── Identity ────────────────────────────────────────────────────────
title              = "Dipteran Wing Image Repository"
description        = "24,852 images of slide-mounted mosquito and tsetse fly wings in 73 taxa, with rich specimen metadata and wing-vein masks for 741 of them."

# ── Catalogue ───────────────────────────────────────────────────────
task               = ["Classification", "Segmentation"]
taxonomic_rank     = "mixed"
class_count        = 73
taxonomic_scope    = ["Diptera"]
background         = ["simple"]
geographic_scope   = "Mostly Germany; also Brazil, Vietnam, Moldova, Latvia, Ukraine, France, Ghana, Côte d'Ivoire, Burkina Faso, Gabon, Pakistan, Peru and Australia, plus laboratory colonies"
composition        = "aggregated"
has_contextual_data = true
contextual_data    = ["location", "collection-date", "trap-metadata", "other"]
year               = 2024
license            = "CC-BY-4.0"
status             = "published"
date               = 2026-10-09

# Optional - delete a line to take the default shown.
developer          = "Kristopher Nolte, Renke Lühken et al. (Bernhard Nocht Institute for Tropical Medicine)"
paper_url          = "https://doi.org/10.1038/s41597-025-05043-3"

# ── Data location ───────────────────────────────────────────────────
doi                = "10.6019/S-BIAD1478"
hosting_status     = "link_only"
commercial_use     = "allowed"

# ── The files this dataset ships. The FIRST one is the link the table shows. ──

[[assets]]
key          = "biostudies-record"
provider     = "biostudies"
url          = "https://www.ebi.ac.uk/biostudies/studies/S-BIAD1478"
released     = 2024-11-12
note         = "The study page, with the description, the authors and the download instructions."

[[assets]]
key          = "images"
provider     = "biostudies"
size_bytes   = 202311390626
url          = "https://ftp.ebi.ac.uk/biostudies/fire/S-BIAD/478/S-BIAD1478/Files/MosquitoWingImages_v2/Files/zipped/"
note         = "14 zips of TIFF images, one per genus. aedes.zip (89 GB) and culex.zip (83 GB) are most of the total."

[[assets]]
key          = "metadata"
provider     = "biostudies"
filename     = "00_metadata_v2.csv"
size_bytes   = 18933017
url          = "https://ftp.ebi.ac.uk/biostudies/fire/S-BIAD/478/S-BIAD1478/Files/MosquitoWingImages_v2/Files/metadata/00_metadata_v2.csv"
note         = "One row per image: the labels and all contextual data. Also published as .xlsx, and as an older v1."

[[assets]]
key          = "segmentation-masks"
provider     = "biostudies"
url          = "https://ftp.ebi.ac.uk/biostudies/fire/S-BIAD/478/S-BIAD1478/Files/MosquitoWingImages_v2/Files/annotations/segmentation_labels/"
note         = "741 PNG masks of the wing veins and outline, named like the image they belong to."
+++

> 24,852 images of slide-mounted mosquito and tsetse fly wings in 73 taxa, with rich specimen metadata and wing-vein masks for 741 of them.

**Intended use.** Benchmarking species identification of disease vectors from
wing images, and automated wing geometric morphometrics. It was assembled to
support vector surveillance: identifying mosquitoes by their wings, where
morphology alone is slow and needs specialists. Every image is a single
dissected wing on a microscope slide, so it is a classification and
segmentation dataset, not a detection one.

## Contents

- **Images:** 24,852 TIFFs of 14,016 specimens. Most specimens have both wings
  imaged, as separate images.
- **Taxa:** 24,532 mosquitoes (Culicidae) in 13 genera, and 320 tsetse flies
  (*Glossina*). The largest genera are *Aedes* (11,154 images), *Culex* (9,297)
  and *Anopheles* (2,416).
- **Labels:** five taxonomic levels per image: family, genus, an aggregate
  level, species and subspecies or biotype. The `TAXA LABEL` column joins them
  into one class name, of which there are 74 spellings for 73 taxa (see
  Limitations). Where species cannot be told apart by morphology, the class is
  a pair, group or complex, e.g. *Culex pipiens* s.l./*torrentium*; a species
  name is given only where a molecular assay confirmed it.
- **Balance:** very uneven. *Cx. pipiens* s.l./*torrentium* alone has 8,318
  images, *Aedes aegypti* 3,807 and *Ae. japonicus* 1,779; 26 taxa have fewer
  than 20 images, several only one.
- **Segmentation masks:** 741 images (*Aedes*, *Culex*, *Anopheles*,
  *Coquillettidia*, *Culiseta*) have a 640 × 320 greyscale PNG tracing the wing
  veins and outline. Edges are anti-aliased, so threshold before use.
- **Landmarks:** the metadata flags 5,691 images as landmark-labelled, but no
  landmark coordinates are in the published files (checked 2026-10-09).

## Sources

A retrospective harmonisation of 33 research projects run between 2008 and
2026. Most images come from the Bernhard Nocht Institute for Tropical Medicine,
Hamburg (20,482); the rest from Fiocruz, Rio de Janeiro (3,318), the University
of Oldenburg (483), EID Méditerranée, Montpellier (429) and the Bundeswehr,
Hamburg (140). The metadata's `Publication DOI` column ties about 9,300 images
to eight earlier publications:

- 10.21203/rs.3.rs-4491538/v1 (3,150 images)
- 10.1186/s13071-023-06038-y (1,279)
- 10.1038/s41598-024-53631-x (1,275)
- 10.1093/jme/tjac139 (1,181)
- 10.21203/rs.3.rs-4747160/v1 (843)
- 10.1128/spectrum.00128-24 (734)
- 10.1038/s41598-020-72873-z (502)
- 10.3390/insects15060393 (380)

## Contextual data

Per image, in `00_metadata_v2.csv`:

- **Location:** a place name, and latitude and longitude for 19,563 images.
- **Collection date:** for 13,271 images, mostly 2016 to 2022.
- **Capture method:** BG-Sentinel, BG-Pro, CDC CO2 light trap, ovitrap,
  aspirator, egg-raft collection, or laboratory colony.
- **Other:** specimen ID, sex, wing side, a damaged-wing flag, how the specimen
  was identified (morphology, qPCR, COI or ITS2 barcoding, or a known
  laboratory colony), imaging device, project, organisation and observer.

Missing values are written `MISSING VALUE`; fields deliberately left empty are
`-`.

## Collection

Wings were removed with tweezers and mounted on microscope slides in Euparal
under a cover slip. They were photographed with three set-ups: an Olympus SZ61
with a DP23 camera (17,006 images, 3088 × 2076), a Leica M205c (6,161 images,
2560 × 1920), and an iPhone SE with a 24× macro lens (1,685 images,
3024 × 3024). Lighting, exposure and background were not standardised and
vary between projects.

## Splits and benchmarks

No official splits, and no benchmark results on the dataset as a whole. The
accompanying paper describes the data; the machine-learning results it cites
come from earlier, separate studies.

When making your own splits, split by `Specimen ID`: the left and right wings
of one specimen are separate images, and putting one in training and the other
in testing leaks the answer. Splitting by project as well is safer, because
project, imaging device and taxa are strongly linked.

## Limitations

- **Imaging is not standardised.** The device and the project correlate with
  the taxa, so a classifier can learn the microscope instead of the wing.
  Hold out whole projects to check.
- **Two wings per specimen.** See Splits above.
- **A duplicate class spelling.** `Culiseta_morsitans-fuminpennis-pair` (22
  images) and `Culiseta_morsitans-fumipennis-pair` (474) are the same taxon.
  Merge them before training: that is why the class count is 73, not 74.
- **Strong imbalance, and mixed levels.** One class holds a third of the images,
  and classes range from single species to species complexes.
- **Mostly females** (21,792 of 24,852 images), and about 7,600 images come from
  laboratory colonies rather than the field.
- **Geography is lopsided.** Mostly Germany and Brazil; 4,346 images have no
  capture location.
- **Wings only.** The images need dissected, slide-mounted wings; models trained
  on them do not transfer to photographs of whole insects.
- **A growing dataset.** New images are added over time, and the DOI always
  points at the latest version. This entry describes the files in
  `MosquitoWingImages_v2` with metadata v2, as of 2026-10-09; the paper
  describes an earlier 18,104 images.

## How to obtain the data

From the EMBL-EBI BioStudies FTP server, over FTP or HTTPS, no registration
required. The images are in 14 zips, one per genus, about 202 GB in total; the
study page recommends `wget` for downloading them. Smaller genera are also
available unzipped, in per-genus folders. The zips contain macOS `__MACOSX`
resource-fork files, which can be ignored.

CC BY 4.0 permits commercial use with attribution. Cite the paper and the
dataset below.

## Citation

```bibtex
@article{nolte2025mosquitowings,
  title   = {Comprehensive Mosquito Wing Image Repository for Advancing Research on Geometric Morphometric- and {AI}-Based Identification},
  author  = {Nolte, Kristopher and Agboli, Eric and Garcia, Gabriela Azambuja and Badolo, Athanase
             and Becker, Norbert and Loc, Do Huy and Dworrak, Tarja Viviane and Eguchi, Jacqueline
             and Eisenbarth, Albert and de Freitas, Rafael Maciel and Doumna-Ndalembouly, Ange Gatien
             and Heitmann, Anna and Jansen, Stephanie and J{\"o}st, Artur and J{\"o}st, Hanna and Kiel, Ellen
             and Meyer, Alexandra and Pfitzner, Wolf-Peter and Saathoff, Joy and Schmidt-Chanasit, Jonas
             and Sulesco, Tatiana and Tokatlian, Artin and Velavan, Thirumalaisamy P.
             and Villaca{\~n}as de Castro, Carmen and Wehmeyer, Magdalena Laura and Zahouli, Julien
             and Sauer, Felix Gregor and L{\"u}hken, Renke},
  journal = {Scientific Data},
  volume  = {12},
  pages   = {715},
  year    = {2025},
  doi     = {10.1038/s41597-025-05043-3}
}

@dataset{nolte2024dipteranwings,
  author    = {Nolte, Kristopher and others},
  title     = {Comprehensive Dipteran Wing Image Repository for Advancing Research on Geometric Morphometric- and {AI}-Based Identification},
  year      = {2024},
  publisher = {EMBL-EBI BioStudies},
  doi       = {10.6019/S-BIAD1478}
}
```
