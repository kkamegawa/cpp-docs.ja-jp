---
title: /Gy (関数レベルのリンクの有効化)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 9643b8b4b4b26b3f7a8a59ed0085601b1a53094d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270725"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (関数レベルのリンクの有効化)

コンパイラが個々の関数をパッケージ関数 (COMDAT) の形式でパッケージ化できるようになります。

## <a name="syntax"></a>構文

```
/Gy[-]
```

## <a name="remarks"></a>Remarks

リンカーは、関数が、除外したり、DLL、または .exe ファイルで個別の関数の順序の Comdat として個別にパッケージ化することが必要です。

リンカー オプションを使用する[/OPT (最適化)](opt-optimizations.md) .exe ファイルから参照されていないパッケージ化された関数を除外します。

リンカー オプションを使用する[/ORDER (順序で配置関数)](order-put-functions-in-order.md)に .exe ファイルで指定した順序でパッケージ化された関数を含めます。

インライン関数は、インスタンスが呼び出される場合に常にパッケージ化されます (が発生する、たとえば、インライン化がオフまたは関数のアドレスを取得する)。 さらに、クラス宣言で定義されている C++ メンバー関数は自動的にパッケージ化されます。その他の関数は使用されませんし、それらをパッケージ化された関数としてコンパイルする必要はこのオプションを選択します。

> [!NOTE]
>  [/ZI](z7-zi-zi-debug-information-format.md) 、エディット コンティニュを使用するオプションが自動的に設定、 **/Gy**オプション。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**コード生成**プロパティ ページ。

1. 変更、**関数レベルのリンクを有効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
