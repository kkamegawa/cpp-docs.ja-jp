---
title: /MD、-MT、-LD (ランタイムライブラリの使用)
ms.date: 07/17/2019
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: 4e734233d94bf57d6838bd4d37c023d55f1d5f6b
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299758"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD、/MT、/LD (ランタイム ライブラリの使用)

マルチスレッド モジュールが DLL であるかどうかを指定し、ランタイム ライブラリのリテール バージョンまたはデバッグ バージョンを指定します。

## <a name="syntax"></a>構文

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Remarks

|オプション|説明|
|------------|-----------------|
|**/MD**|アプリケーションでランタイム ライブラリのマルチスレッド対応および DLL 対応バージョンが使用されます。 `_MT` および `_DLL` を定義し、コンパイラにライブラリ名 MSVCRT.lib を .obj ファイルに挿入させます。<br /><br /> このオプションを使用してコンパイルされたアプリケーションは、MSVCRT.lib に静的にリンクされます。 このライブラリには、リンカーが外部参照を解決できるようにするコード レイヤーが用意されています。 実際の作業コードは、MSVCR*versionnumber*に含まれています。DLL。実行時に、MSVCRT.DLL にリンクされているアプリケーションに対して使用可能である必要があります。|
|**/MDd**|`_DEBUG`、`_MT`、および `_DLL` を定義します。アプリケーションで、マルチスレッド対応バージョンおよび DLL 対応バージョンのランタイム ライブラリが使用されます。 また、コンパイラによって、ライブラリ名 MSVCRTD.lib が .obj ファイルに挿入されます。|
|**/MT**|アプリケーションで、マルチスレッド バージョンの静的なランタイム ライブラリが使用されます。 `_MT` を定義します。また、コンパイラにライブラリ名 LIBCMT.lib を .obj ファイルに挿入させるため、リンカーは LIBCMT.lib を使って外部シンボルを解決します。|
|**/MTd**|`_DEBUG` および `_MT` を定義します。 このオプションによって、リンカーが LIBCMTD.lib を使用して外部シンボルを解決できるように、コンパイラによりライブラリ名 LIBCMTD.lib が .obj ファイルに挿入されます。|
|**/LD**|DLL を作成します。<br /><br /> リンカーに **/dll**オプションを渡します。 リンカーは `DllMain` 関数の有無を確認します。 `DllMain` 関数が記述されていないと、TRUE を返す `DllMain` 関数がリンク時に自動的に挿入されます。<br /><br /> DLL の起動コードをリンクします。<br /><br /> コマンド ラインでエクスポート (.exp) ファイルが指定されていない場合は、インポート ライブラリ (.lib) を作成します。 このインポート ライブラリを、DLL を呼び出すアプリケーションにリンクしてください。<br /><br /> [/Fe (名前付き Exe ファイル)](fe-name-exe-file.md)を .exe ファイルではなく DLL に名前を付けて解釈します。 既定では、プログラム名は、*ベース*名ではなく、.dll*になります*。<br /><br /> **/Md**を明示的に指定しない限り、 **/mt**を意味します。|
|**/LDd**|デバッグ DLL を作成します。 `_MT` および `_DEBUG` を定義します。|

C ランタイムライブラリと、 [/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md)を使用してコンパイルするときに使用されるライブラリの詳細については、「 [CRT ライブラリの機能](../../c-runtime-library/crt-library-features.md)」を参照してください。

リンカーの特定の呼び出しに渡されるすべてのモジュールは、同じランタイムライブラリコンパイラオプション ( **/md**、 **/mt**、 **/ld**) を使用してコンパイルされている必要があります。

ランタイムライブラリのデバッグバージョンを使用する方法の詳細については、「 [C ランタイムライブラリリファレンス](../../c-runtime-library/c-run-time-library-reference.md)」を参照してください。

Dll の詳細については、「 [Visual Studio での C/C++ dll の作成](../dlls-in-visual-cpp.md)」を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[コード生成]** プロパティページを選択します。

1. **ランタイムライブラリ**のプロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
