# Archive of TG.no (TG25 and beyond)

Archive of TG25 site using WARC standard. See [./browsertrix-crawler](browsertrix-crawler) folder for files and details.

# Browsertrix-crawler (Webrecorder tools)

Generated using [go-archive](https://github.com/gathering/go-archive) repo that uses [browsertrix-crawler](https://github.com/webrecorder/browsertrix-crawler) to
generates an interactive (and timetravelable) archive using the WARC (Web
ARChive) standard.

## Capturing

To capture a new snapshot of gathering.org run the crawler command in
`go-archive` repo with `tgno`s crawl configuration file. Then update this repo
with additional archive files generated.

PS. As we start using WARC as our new archive standard, we expect to transition to
a semi-automatic archive setup, where we generate snapshots of the site on a
set interval.

## Displaying

The recommended setup is just running `go-archive` repo/service since that is
the known working setup that is used on [Gathering.org archive](https://archive.gathering.org).

To run manually install [pywb](https://github.com/webrecorder/pywb) and use the
`wayback` command and a local collection configuration file (see their docs or
examples in `go-archive`).

Due to size of repo/files we use [Git LFS](https://git-lfs.github.com/) for storage of WARC files.
