# libxml2.vcpkg

Este pacote NuGet **redistribui** a biblioteca **libxml2** (versão fixada em [`vcpkg.json`](vcpkg.json)), compilada com o [vcpkg](https://github.com/microsoft/vcpkg) para **Windows x64** usando o **Microsoft Visual Studio 2022 (toolset v143)**.

> Este é um pacote não-oficial de empacotamento. Não é afiliado nem endossado pelo Projeto GNOME, pelos autores do libxml2 ou pela Free Software Foundation.

## 📦 Conteúdo do pacote

- Arquivos de cabeçalho (`include/libxml/*.h`)
- Bibliotecas estáticas:
  - `libxml2.lib`
  - `charset.lib`
  - `iconv.lib`
  - `lzma.lib`
  - `zlib.lib` (ou `zlibd.lib` no modo Debug)
- Bibliotecas dinâmicas (`.dll`) para Debug e Release
- Arquivo `.targets` que configura automaticamente:
  - Include paths
  - Lib paths
  - Dependências
  - Cópia dos `.dll` para a pasta de saída

## ⚙️ Como usar

1. Adicione o pacote ao seu projeto C++ via NuGet:

2. O Visual Studio aplicará automaticamente as configurações via o arquivo `.targets` incluído.

3. Certifique-se de que o projeto esteja em plataforma **x64**.

## 🔁 Configuração automática

- Em `Release`: links com `zlib.lib`
- Em `Debug`: links com `zlibd.lib`
- As DLLs são copiadas para `$(OutDir)` após o build

## 📝 Licenças

Este pacote redistribui binários de terceiros. A expressão SPDX do pacote é:

```text
MIT AND Zlib AND 0BSD AND LGPL-2.1-or-later
```

| Componente | Licença | Binários |
| --- | --- | --- |
| [libxml2](https://gitlab.gnome.org/GNOME/libxml2) | [MIT](https://spdx.org/licenses/MIT.html) | `libxml2.dll` / `.lib`, headers |
| [zlib](https://zlib.net/) | [Zlib](https://spdx.org/licenses/Zlib.html) | `zlib1.dll`, `zlib.lib` / `zlibd.lib` |
| [liblzma (XZ Utils)](https://tukaani.org/xz/) | [0BSD](https://spdx.org/licenses/0BSD.html) | `lzma.dll` / `.lib` |
| [GNU libiconv](https://www.gnu.org/software/libiconv/) | [LGPL-2.1-or-later](https://spdx.org/licenses/LGPL-2.1-or-later.html) | `iconv.dll`, `charset.dll` + import libs |

Os textos completos das licenças acompanham o `.nupkg` na pasta `licenses/`.

**Aviso LGPL.** `iconv.lib` e `charset.lib` são *import libraries* — o link com o
libiconv é **dinâmico**. Você pode licenciar sua aplicação como quiser, e pode
exercer o direito de relink (LGPL-2.1 §6) simplesmente substituindo
`iconv.dll` / `charset.dll` na pasta de saída pela sua própria build do libiconv.
Detalhes e atribuição completa em [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

Os arquivos de empacotamento deste repositório (`.nuspec`, `.targets`, `.vcxproj`,
workflow) são de autoria de Dario Alves Junior e estão sob [MIT](LICENSE).
Essa licença cobre **apenas** o empacotamento — não relicencia os binários upstream.

## 🔗 Links úteis

- Site oficial: <http://xmlsoft.org/>
- Fonte: <https://gitlab.gnome.org/GNOME/libxml2>
- vcpkg: <https://github.com/microsoft/vcpkg>
