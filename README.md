# Cascade IPTV: libVLC corresponding source

This repository provides the corresponding source code for the libVLC binaries
shipped with **Cascade IPTV for Windows**, published by CNR Nexus Consulting Inc.

libVLC and the libraries inside it are licensed under the GNU Lesser General
Public License (version 2.1 or later, and version 3 for some libraries). This
repository exists to meet that licence. Cascade IPTV itself is a separate,
proprietary application and its source is not included here.

## What was built

| Item | Value |
|---|---|
| Upstream | VideoLAN VLC, tag `3.0.23-2` (commit `79128878ddb2c280bbb6c89c76a46b31a80ade1c`) |
| Target | Windows x64 (`x86_64-w64-mingw32`) |
| Toolchain image | `registry.videolan.org/vlc-debian-win64-3.0:20251208092116` |
| Build script | `extras/package/win32/build.sh -a x86_64 -r -z -i z -o <prefix>` |

GPL-licensed components were excluded:

- Third-party libraries (contribs) were bootstrapped with `--disable-gpl --enable-ad-clauses`, so FFmpeg is LGPL.
- VLC plugins whose sources are GPL were not shipped.
- The Yadif mode was removed from the deinterlace plugin (its sources carry a GPL header).

The exact changes to the VLC tree are in [`cascade-vlc.patch`](cascade-vlc.patch).
Contrib and configure flags are in [`BUILD-INFO.txt`](BUILD-INFO.txt).

## Getting the full source

See the [Releases](../../releases) page. Each release contains:

- `vlc-3.0.23-2-cascade-lgpl.tar.gz`: the VLC source tree as built, with the patch applied.
- `vlc-contrib-tarballs-3.0.23-2.tar`: the source archives of every third-party library the build downloads.
- `cascade-vlc.patch` and `BUILD-INFO.txt`.

The release is produced by the [publish-source workflow](.github/workflows/publish-source.yml) from the upstream tag, so anyone can reproduce it.

## Written offer

We will also provide this source on request for at least three years after you
received the corresponding version of Cascade IPTV. Contact: info@cnrnexus.consulting

VLC and VideoLAN are trademarks of VideoLAN. This project is not affiliated with or endorsed by VideoLAN.
