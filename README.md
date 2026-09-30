# InsectAI Benchmark Datasets

A registry of insect image datasets for benchmarking detection, classification
and segmentation models. Data stays with its authors, this catalogue points at it
and never redistributes it.

The site, its schema rules and its contribution workflow follow the
[InsectAI Model Database](https://github.com/InsectAI-COST-Action/model-db), and reuse
its site code.

## Dataset metadata is stored as an .md file

A dataset is **one file**: `content/datasets/<id>/index.md`. Its front matter is
the registry record, the fields the website renders, and the prose beneath it is
the dataset card.

**The build is the validator.** Hugo checks every card against
[`data/schema.toml`](data/schema.toml) as it renders, and stops with a message
naming the file, the field and what it wanted. There is no separate check
command to remember, and no way to publish a card that has not been checked.

## Quickstart

Install **Hugo extended**, the plain build cannot run the asset pipeline in
`layouts/partials/head.html`, so the site would ship without its stylesheet or
its script.

| Platform | Install |
| --- | --- |
| Linux | `./scripts/fetch-hugo.sh` one-time, downloads into `./bin` |
| macOS | `brew install hugo` |
| Windows | `winget install Hugo.Hugo.Extended` |

Then start the preview:

```bash
./scripts/serve.sh          # → http://localhost:1313/
```

`serve.sh` uses `./bin/hugo` if it is there and a `hugo` on your PATH
otherwise. To run Hugo directly instead, keep the `--baseURL` override that puts
the preview at the site root:

```bash
hugo server --baseURL http://localhost:1313/
```

## Adding a dataset

**Read [contributing](content/contributing.md), or in short:**

```bash
cp -r template content/datasets/my-dataset
# edit content/datasets/my-dataset/index.md, then set status = "published" when ready
./scripts/serve.sh
```

## Repository layout

```
content/datasets/<id>/index.md   the whole entry: front matter + dataset card
content/datasets/<id>/LICENSE    the upstream license, where it is separate
template/                        what you copy to start a new dataset
data/schema.toml                 every field, and the values each accepts
layouts/                         hand-written templates; no theme, no mounts
assets/css, assets/js            the site's only stylesheet and only script
scripts/                         fetch-hugo.sh, serve.sh
```

## Pointing at the dataset's own card

When a dataset already has a card on Hugging Face, this entry points at it
instead of copying it:

```toml
hf_repo     = "imageomics/TreeOfLife-10M"
hf_revision = "0123456789abcdef0123456789abcdef01234567"
```

The site shows **both** links, the pinned revision the entry was curated
against, and the authors' current version. `hf_revision` is a commit hash: the
build rejects a branch name, because the license and commercial-use terms in the
entry are claims about what that card said at the time, and a branch can move
while the entry stays put. Pinning is what keeps the claim checkable.

Refreshing it is a deliberate act: update the hash, and the change lands as a
reviewable diff in a pull request.

## Why the schema is small

**A field exists only if the website renders it.** Whatever else is useful
about a dataset belongs in the card's prose, where it can be written as a
sentence. Fourteen fields are required, and one more when it applies; everything else has a default, so a
contributor who does not know the answer can delete the line.
