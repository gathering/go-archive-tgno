# The Gathering - TG.no archive

Web archive of [www.tg.no](https://www.tg.no) in the WARC standard, from the
launch of the site in October 2024 (TG25) onwards. Served at
https://archive.tg.no.

tg.no is one site that is updated continuously, not a new site each year, so
this archive is a series of crawls of the same site taken at different dates
(before ticket sale, mid event, after event, ...).

## Contents

```
tgno/
  archive/   WARC files, stored in Git LFS
  records/   one folder per crawl
```

**`tgno/archive/`**: files are named `rec-<crawl id>-tgno-<timestamp>-<n>.warc.gz`.
All files with the same crawl id belong to the same crawl.

**`tgno/records/<date>-<time>-<label>/`**: one folder per crawl, made from the
crawler's own output:

- `crawl-*.yaml` or `*-tgno.yaml`: the crawler's state file. It contains the
  config the crawl ran with, and the list of URLs that were crawled.
- `pages.jsonl`, `extraPages.jsonl`: every crawled page with title, status code
  and timestamp.
- `record.json`: label, the commit of [go-archive](https://github.com/gathering/go-archive)
  that ran the crawl, crawler image, and extra crawler arguments. Records with
  `"reconstructed": true` were made afterwards for crawls from before this
  folder existed, from the files that were stored here at the time (git history
  has the originals). They have the label and commit of this repo, and the
  crawler version where an old log was available.

Indexes, logs, the browser profile and the crawler's other working files are not
committed. pywb builds its indexes from the WARC files when serving.

## Viewing the archive

Requires [Git LFS](https://git-lfs.github.com/) (`git lfs install`, then `git lfs pull`).

With the tooling in [go-archive](https://github.com/gathering/go-archive), point
`ARCHIVE_DIR` at this repo and run:

```
ARCHIVE_DIR=/path/to/go-archive-tgno ARCHIVES=tgno ./archive serve
```

then open http://localhost:8080/tgno/https://www.tg.no/.

## Adding a crawl

Crawls are made with go-archive:

```
./archive crawl --label "tg27 opening"
./archive publish work/<crawl dir>
```

`publish` copies the new WARC files into `tgno/archive/` and writes the crawl
record into `tgno/records/`. Commit both, with a message like `feat: tg27
opening crawl`, and push. WARC files are tracked by Git LFS (`.gitattributes`).
