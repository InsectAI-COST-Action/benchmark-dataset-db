+++
# ═══════════════════════════════════════════════════════════════════════════════
#  A dataset card for the InsectAI Benchmark Datasets registry.
# ═══════════════════════════════════════════════════════════════════════════════
#
#  To add a dataset:
#
#      cp -r template content/datasets/your-dataset-id
#      #  edit content/datasets/your-dataset-id/index.md
#      ./scripts/serve.sh
#
#  Name the folder in kebab-case. A dataset with a name of its own uses it. A
#  dataset known only as "the one from that paper" uses
#  <firstauthor>-<year>-<descriptor>, e.g. `smith-2024-light-trap-moths`.
#
#  Everything between the +++ lines is checked when the site builds. Get one
#  wrong and the build stops and tells you which file and what to write, in
#  plain language. You do not have to run a separate command to find out.
#
#  Every field the site displays is in this file. Anything else you want to say
#  goes in the prose below the closing +++, where you can say it in a sentence
#  instead of in a field.

# ── Identity ──────────────────────────────────────────────────────────────────

title              = "REPLACE WITH THE DATASET NAME"
description        = "One sentence, in plain language, saying what the dataset contains."

# ── Catalogue ─────────────────────────────────────────────────────────────────

task               = ["Detection"]               # Detection | Classification | Segmentation.
                                                 # List every task the annotations support.
                                                 # A task not listed here? Add it to the
                                                 # task values in data/schema.toml first.

# What the dataset covers. Be as specific as you can: the table shows these as
# e.g. "1000 genera" above the taxonomic scope.
taxonomic_rank     = "species"                   # species | genus | family | order | mixed |
                                                 # generic (one untaxonomic class such as
                                                 # "insect", as in a detector that finds
                                                 # insects without naming them)
class_count        = 1                           # how many distinct classes, no quotes
taxonomic_scope    = "REPLACE"                   # which insects, e.g. "Coleoptera: Carabidae"
                                                 # or "Bumblebees (Bombus)". Not just "insects".
background         = ["simple"]                  # simple | complex. simple = light trap, sticky
                                                 # trap, tray or lab surface; complex = field
                                                 # imagery. List both if it has both.
geographic_scope   = "REPLACE"                   # where the images were taken, e.g. "Denmark",
                                                 # "Global". "Not stated" if the source is silent.
composition        = "self-contained"            # self-contained | aggregated (assembled from
                                                 # several datasets: name them under Sources)

# Contextual data: anything beyond the images and their labels.
has_contextual_data = false                      # true | false, no quotes
# contextual_data   = ["location"]               # REQUIRED if has_contextual_data = true, and
                                                 # must be left out if false. Any of:
                                                 # location | collection-date | time-of-day |
                                                 # genetic | environmental | trap-metadata |
                                                 # morphological | other

year               = 2025                        # year of publication or release
license            = "CC-BY-4.0"                 # SPDX identifier where one exists
status             = "draft"                     # draft | published | deprecated.
                                                 # Draft is the safe default: only
                                                 # `published` appears on the site.

# Optional. Delete any line you do not have an answer for - the default is in
# the comment.
date               = 2026-09-30                  # when this entry was added to the registry
developer          = "REPLACE"                   # who made it, not who curated it
paper_url          = ""                          # paper or project page

# ── Data location ─────────────────────────────────────────────────────────────

doi                = ""                          # the DATASET's DOI, bare: "10.5281/zenodo.1234567"
commercial_use     = "unknown"                   # allowed | prohibited | permission_required | unknown

# Where to download the dataset. The FIRST block is the link the catalogue table
# shows, and its provider is shown as the dataset's host. Add another only if the
# dataset genuinely ships as several files, e.g. images and annotations apart.
#
# Data is never committed here. GitHub refuses files over 100 MB and the
# authors host it anyway.

[[assets]]
key      = "images"               # the label shown in the sidebar
provider = "zenodo"               # zenodo | huggingface | github | erda | kaggle | figshare |
                                  # dryad | gbif | url | google-drive | dropbox
url      = "https://..."
# Optional, and worth adding when you know them:
# filename   = "images.zip"
# size_bytes = 6275129
# sha256     = "..."
# released   = 2024-10-23
# note       = "What this file holds, and anything a downloader should know."

# ── The dataset's own card, if it has one elsewhere ───────────────────────────
#
# If the authors already keep a card on Hugging Face, point at it rather than
# copying it here - a copy starts drifting the moment they edit theirs.
#
# hf_revision is a COMMIT HASH, not a branch. Find it under "History" in the
# dataset's "Files and versions" tab. A branch name can move, and the license
# and commercial-use terms recorded above are what that card said when this
# entry was curated; pinning is what keeps that claim checkable.
#
# The site then shows both links: the pinned revision as curated, and the
# authors' current version.

hf_repo     = ""
hf_revision = ""
+++

<!--
  Do not repeat the dataset name as a heading - the page renders it already.

  The sections below are a convention, not a rule: nothing checks for them.
  They exist so two entries in the registry can be read side by side. Delete any
  that do not apply, and add whatever does.
-->

**Intended use.** One or two sentences on what this dataset is for, and the
question it was collected to answer. A reader who is scanning five entries
should be able to tell from this paragraph whether this one is theirs.

## Contents

How many images, how many annotations, and of what: boxes, masks or labels.
Name the taxa and the level they are labelled at (species, genus, family), and
how evenly the images are spread across them.

## Sources

Delete this section for a self-contained dataset. For an aggregated one, list
the datasets it was assembled from, with a link or citation for each.

## Contextual data

Delete this section if the dataset is images and labels only. Otherwise say what
comes with the images, per image or per specimen: coordinates and their
precision, collection dates, DNA barcodes and where they are deposited, and so on.

## Collection

How the images were captured (camera, trap type, lab or field), where and when,
and at what resolution. Anything about the setup that would make a model trained
elsewhere struggle is worth saying.

## Splits and benchmarks

Whether the authors publish official train/validation/test splits, and which
metric results are reported with. Name any models already evaluated on it, and
their scores **as the source publication reports them**. If there are no
official splits, say so: results on ad-hoc splits are not comparable.

## Limitations

**This is the section that matters most.** An empty limitations section is worse
than no card at all, because it implies somebody checked. Say what the dataset
does not cover: taxa, life stages, regions, seasons, backgrounds, image quality,
and any known labelling errors.

## How to obtain the data

Where it lives, what the license actually permits, and whether the link is
pinned. Say here if there is anything a downloader has to do: register, request
access, accept terms, reassemble split archives.

## Citation

BibTeX, or the reference as the authors would want it cited.
