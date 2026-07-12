# licenses/

Verbatim license texts for every third-party component redistributed by the
`libxml2.vcpkg` NuGet package. These files ship inside the `.nupkg` under
`licenses/`, which is how the package satisfies its attribution obligations —
the LGPL of libiconv in particular requires the license text to accompany the
binary.

| File | Component | SPDX | Source |
| --- | --- | --- | --- |
| `libxml2.txt` | libxml2 | `MIT` | [`Copyright`](https://gitlab.gnome.org/GNOME/libxml2/-/raw/master/Copyright) |
| `libiconv.txt` | GNU libiconv / libcharset | `LGPL-2.1-or-later` | [`COPYING.LIB`](https://git.savannah.gnu.org/cgit/libiconv.git/plain/COPYING.LIB) |
| `zlib.txt` | zlib | `Zlib` | [`LICENSE`](https://raw.githubusercontent.com/madler/zlib/develop/LICENSE) |
| `liblzma.txt` | liblzma (XZ Utils) | `0BSD` | [`COPYING.0BSD`](https://raw.githubusercontent.com/tukaani-project/xz/master/COPYING.0BSD) |
| `packaging-MIT.txt` | this repo's packaging files | `MIT` | copied from `../LICENSE` at pack time |

These committed copies exist so the repository is auditable and so `nuget pack`
works locally. They are **not** the copies that get shipped: the
`Collect third-party license texts` step in
[`../.github/workflows/build-nuget.yml`](../.github/workflows/build-nuget.yml)
overwrites each one with the text vcpkg installs at
`vcpkg_installed/x64-windows/share/<port>/copyright` — the exact license of the
exact revision that was built. The build fails if any required component has no
license text, so a binary can never ship without one.

Attribution and the LGPL relink notice live in
[`../THIRD-PARTY-NOTICES.md`](../THIRD-PARTY-NOTICES.md).

Do not hand-edit the `.txt` files. To refresh them, re-download from the sources
above.
