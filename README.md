# libxml2.vcpkg

Este pacote NuGet fornece a biblioteca **libxml2** versão **2.11.5**, compilada com o [vcpkg](https://github.com/microsoft/vcpkg) para **Windows x64** usando o **Microsoft Visual Studio 2022 (toolset v143)**.

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

## 📝 Licença

- **libxml2**: [MIT License](http://www.opensource.org/licenses/mit-license.html)
- Este pacote NuGet: [Apache-2.0](https://spdx.org/licenses/Apache-2.0.html)

## 🔗 Links úteis

- Site oficial: http://xmlsoft.org/
- Fonte: https://github.com/GNOME/libxml2
- vcpkg: https://github.com/microsoft/vcpkg
