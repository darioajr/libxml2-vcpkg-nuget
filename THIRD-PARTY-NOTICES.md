# Third-Party Notices

The NuGet package `libxml2.vcpkg` **redistributes binaries built from third-party
open source projects**. It is not an original work; it is a repackaging of
upstream sources built with [vcpkg](https://github.com/microsoft/vcpkg).

The verbatim license text for every redistributed component is included in the
package under the `licenses/` folder, copied directly from the corresponding
vcpkg port (`share/<port>/copyright`).

SPDX expression for the package as a whole:

```text
MIT AND Zlib AND 0BSD AND LGPL-2.1-or-later
```

---

## Redistributed components

### libxml2 — MIT

- Copyright (C) 1998-2012 Daniel Veillard. All Rights Reserved.
- Homepage: <https://gitlab.gnome.org/GNOME/libxml2>
- SPDX: `MIT`
- Full text: `licenses/libxml2.txt`
- Binaries: `libxml2.dll`, `libxml2.lib`, headers under `include/libxml/`

### GNU libiconv (libiconv + libcharset) — LGPL-2.1-or-later

- Copyright (C) 1999-2019 Free Software Foundation, Inc.
- Homepage: <https://www.gnu.org/software/libiconv/>
- SPDX: `LGPL-2.1-or-later`
- Full text: `licenses/libiconv.txt`
- Binaries: `iconv.dll`, `charset.dll`, `iconv.lib`, `charset.lib`

**LGPL notice.** libiconv and libcharset are covered by the GNU Lesser General
Public License. This package links them **dynamically**: `iconv.lib` and
`charset.lib` are *import libraries* for `iconv.dll` and `charset.dll`, not
static archives. Consumers of this package therefore link against the LGPL code
dynamically, and are free to license their own application under terms of their
choosing.

Under LGPL-2.1 section 6, you are entitled to **modify libiconv and relink your
application against your modified version**. Because the linkage is dynamic, you
can exercise this right by replacing `iconv.dll` / `charset.dll` in your output
directory with your own build of libiconv, without any changes to your
application. Unmodified upstream sources are available at
<https://ftp.gnu.org/pub/gnu/libiconv/> and the exact build recipe used here is the
vcpkg `libiconv` port at the baseline commit pinned in `vcpkg-configuration.json`.

If you do **not** want any copyleft-licensed component in your dependency tree,
build libxml2 yourself with the `iconv` feature disabled; note that doing so
removes support for legacy character encodings.

### zlib — Zlib

- Copyright (C) 1995-2024 Jean-loup Gailly and Mark Adler
- Homepage: <https://zlib.net/>
- SPDX: `Zlib`
- Full text: `licenses/zlib.txt`
- Binaries: `zlib1.dll`, `zlib.lib` (Release) / `zlibd.lib` (Debug)

### liblzma (XZ Utils) — 0BSD

- Homepage: <https://tukaani.org/xz/>
- SPDX: `0BSD` (older releases: public domain)
- Full text: `licenses/liblzma.txt`
- Binaries: `lzma.dll`, `lzma.lib`

---

## Packaging files

The packaging glue in this repository — `libxml2.nuspec`, `libxml2.vcpkg.targets`,
`libxml2.vcxproj`, `vcpkg.json`, and the GitHub Actions workflow — is authored by
Dario Alves Junior and licensed under the MIT License (see `LICENSE`, shipped in
the package as `licenses/packaging-MIT.txt`).

That grant applies **only** to those packaging files. It does **not** apply to,
and does not relicense, any of the redistributed upstream binaries or headers
listed above, which remain under their own licenses.
