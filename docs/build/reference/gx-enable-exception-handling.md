---
title: /GX (例外処理の有効化)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245088"
---
# <a name="gx-enable-exception-handling"></a>/GX (例外処理の有効化)

非推奨。 `extern "C"` を使用して宣言された関数が例外をスローしないことを想定して、同期例外処理を有効にします。

## <a name="syntax"></a>構文

```
/GX
```

## <a name="remarks"></a>コメント

**/Gx**は非推奨とされます。 代わりに、 [/ehsc](eh-exception-handling-model.md)オプションを使用してください。 非推奨のコンパイラオプションの一覧については、「[カテゴリ別のコンパイラオプション](compiler-options-listed-by-category.md)」の「**非推奨のコンパイラオプション**」セクションを参照してください。

既定では、 **/ehsc**は **/gx**に相当しますが、Visual Studio 開発環境を使用してコンパイルすると有効になります。 コマンドラインツールを使用する場合、例外処理は指定されません。 これは、 **/GX-** に相当します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. ナビゲーションウィンドウで、 **[構成プロパティ]** 、 **[CC++/]** 、 **[コマンドライン]** の順に選択します。

1. [追加のオプション] ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>」を参照してください。

## <a name="see-also"></a>参照

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/EH (例外処理モデル)](eh-exception-handling-model.md)
