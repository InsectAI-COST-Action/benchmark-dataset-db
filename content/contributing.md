---
title: Adding a dataset
description: How to add a dataset to the registry, starting from the template, and what to write in the card.
---

Adding a dataset takes three steps. You need a terminal, but you do not need to
install anything, and there is nothing to run afterwards that tells you whether
you got it right: **the site build is the check.** If something is wrong, it
stops and says which field and what to write instead.

## 1. Copy the template folder

```bash
cp -r template content/datasets/my-dataset
```

Name the folder in kebab-case (lowercase with hyphens). A dataset with a name of
its own uses it. A dataset known only as "the one from that paper" uses
`<firstauthor>-<year>-<descriptor>`, such as `smith-2024-light-trap-moths`.

## 2. Edit `content/datasets/my-dataset/index.md`

That one file is the whole entry to be compiled. The fields at the top are
what the catalogue table, the filters and the sidebar are built from. The
prose below them is the dataset card proper.

Every field has a comment beside it explaining what it wants. Some additional
guidelines:

- **`status` starts as `draft`.** Only `published` appears on the site, so a
  half-finished entry is invisible until it is set to `published`.
- **`task` lists every task the annotations support.** A dataset with boxes and
  species labels writes `task = ["Detection", "Classification"]`, and shows up
  under either one in the home page's Task filter. If your dataset supports a
  task the registry does not have yet, add it to the `task` values in
  `data/schema.toml` first, then build.
- **Be specific about the taxa.** `taxonomic_rank` and `class_count` together
  say what the labels are, e.g. `"genus"` and `1000` for a dataset of 1000
  genera. A detector that finds insects without naming them uses `"generic"` and
  `1`. `taxonomic_scope` then names the group: "Coleoptera: Carabidae", not
  "insects".
- **`background` can list both values.** A dataset mixing trap images and field
  photographs writes `background = ["simple", "complex"]`.
- **`composition` is `aggregated`** if the dataset was assembled from several
  separate datasets. Name them in the card's Sources section.
- **Contextual data is a yes/no, then a list.** Set `has_contextual_data = true`
  if the dataset comes with anything beyond images and labels, such as location,
  dates or DNA, and then list it in `contextual_data`. The build requires the
  list when the answer is `true` and refuses it when it is `false`.
- **`doi` is the dataset's DOI, not the paper's**, written bare:
  `doi = "10.5281/zenodo.1234567"`.

Data is never committed here. Point `url` at Zenodo, ERDA, Hugging Face or any
other downloadable location.

## 3. Look at it

```bash
./scripts/serve.sh          # → http://localhost:1313/
```

If the build stops, read the message: it names the file, the field, and what it
wanted. Fix it and save, then Hugo rebuilds on its own.

## If the dataset already has a card on Hugging Face

Point at it rather than copying it. A copy starts drifting the moment the
authors edit theirs.

```toml
hf_repo     = "imageomics/TreeOfLife-10M"
hf_revision = "0123456789abcdef0123456789abcdef01234567"
```

`hf_revision` is a **commit hash, not a branch**. It can be found under
"History" in the dataset's "Files and versions" tab on Hugging Face. The build
refuses a branch name or a missing hash. That is deliberate: the license and
commercial-use terms you record above are what that card said when you curated
this entry, and a branch can move underneath that claim while the entry stays
put.

The site then shows both links: the revision as curated, and the authors'
current version, so a reader who wants the latest can still get it.

You still write a local card. Keep it short if the upstream one is good, but
say what a *reader of this registry* needs, particularly splits, limitations
and license.

## Writing the card

The headings in the template are a convention, not a rule. Nothing checks for
them. They exist so two entries can be read side by side.

## Where to get help

The build error is the help. It names the file, the field and the fix. If it
does not make sense, the field list with explanations is in
[`data/schema.toml`](https://github.com/saij19/benchmark-dataset-db/blob/main/data/schema.toml).
Open it, find the field that is raising the error, and read what it says.
