# socat-build

This project contains build scripts for the [socat](http://www.dest-unreach.org/socat/)
open source utility, and runs them from GitHub Actions to provide prebuilt binaries.

Short about socat, from the [man page](http://www.dest-unreach.org/socat/doc/socat.html):

> Socat is a command line based utility that establishes two bidirectional byte streams
and transfers data between them. Because the streams can be constructed from a large
set of different types of data sinks and sources (see address types), and because lots
of address options may be applied to the streams, socat can be used for many different
purposes.

The primary focus for the builds provided by this project is to enable easy creation of
different customized and minimalistic variants, that only include a specific set of
socat's around 35 optional features.

The binaries are built stripped and statically linked, and the GitHub Action automatic
builds for linux run the scripts in an Alpine container image, which makes the resulting
binaries of minimum size and maximum portability across different Linux distros - since
Alpine uses musl as C standard library.

Windows binaries are also built. These are built from the same build scripts, using
a MSYS2 environment. This leads to a dependency to the MSYS2 runtime library msys-2.0.dll,
which is bundled together with socat.exe in the artifact.

### Binaries

You can find prebuilt binaries in the [Releases](https://github.com/albertony/socat-build/releases)
section. My current strategy is to publish binaries in a single release, named "Binaries",
which I replace whenever a new complete, successful build has been performed. The binaries
in the release are taken from a workflow run, which you can find in the
[Actions](https://github.com/albertony/socat-build/actions) section. While the release
does not contain much information, the workflow runs will give you all the details from
the build and about the artifacts produced. You can also find older runs, and download
their artifacts, but there is a retention period for these artifacts, currently 30 days,
while the assets on the release will be permanently available.

### Disclaimer

This is a work in progress, and sort of a test bench at the moment. I *will* break things,
and perform rebase and force-push the git repo, etc.