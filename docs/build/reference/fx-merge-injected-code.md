---
title: /Fx (挿入されたコードのマージ)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: f1a266eee4edc524fbbe49bdef31a8235f62bd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292303"
---
# <a name="fx-merge-injected-code"></a>/Fx (挿入されたコードのマージ)

挿入されたコードをソースにマージして、各ソース ファイルのコピーを生成します。

## <a name="syntax"></a>構文

```
/Fx
```

## <a name="remarks"></a>Remarks

**/Fx** では、元のソース ファイルとマージされたソース ファイルを区別するため、ファイル名とファイル拡張子の間に .mrg 拡張子を追加します。 たとえば、属性付きのコードを含んだ MyCode.cpp という名前のファイルを **/Fx** でビルドすると、次のコードを含んだ MyCode.mrg.cpp という名前のファイルが作成されます。

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

.mrg ファイルでは、属性により挿入されたコードは次のように区切られます。

```
//+++ Start Injected Code
...
//--- End Injected Code
```

[no_injected_text](../../windows/no-injected-text.md) 属性が .mrg ファイルに埋め込まれることにより、テキストを再挿入せずに .mrg ファイルのコンパイルができます。

.mrg ソース ファイルは、コンパイラによって挿入されたソース コードの表示を目的としていることに留意する必要があります。 .mrg ファイルは元のソース ファイルと完全に同じようにはコンパイルまたは実行されない場合があります。

.mrg ファイルでは、マクロは展開されません。

挿入されたコードを使用するヘッダー ファイルがプログラムに含まれている場合、 **/Fx** はそのヘッダー用の .mrg.h ファイルを生成します。 **/Fx** は、挿入されたコードを使用しないインクルード ファイルをマージしません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[出力ファイル]** プロパティ ページをクリックします。

1. **[属性ソースの展開]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
