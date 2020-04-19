---
title: /Og (グローバルの最適化)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: 5e45273b6b609f1bf78504a519c1fb98e2147f76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320293"
---
# <a name="og-global-optimizations"></a>/Og (グローバルの最適化)

非推奨。 ローカルとグローバルの最適化を提供して自動レジスタ割り当て、および最適化をループします。 いずれかを使用することをお勧めします。 [/O1 (サイズを最小限に抑える)](o1-o2-minimize-size-maximize-speed.md)または[/O2 (速度)](o1-o2-minimize-size-maximize-speed.md)代わりにします。

## <a name="syntax"></a>構文

> /Og

## <a name="remarks"></a>Remarks

**/Og**は非推奨とされます。 これらの最適化は既定では一般的に有効になりました。 最適化の詳細については、次を参照してください。 [/O1、/O2 (サイズの最小化、速度の最大化)](o1-o2-minimize-size-maximize-speed.md)または[/Ox (有効にする最もの速度の最適化)](ox-full-optimization.md)します。

次の最適化は **/Og**:

- ローカルとグローバルの共通部分式の削除

   この最適化では、共通部分式の値が 1 回計算されます。 次の例では場合の値`b`と`c`3 つの式の間で変更しないで、コンパイラでの計算を割り当てることができます`b + c`一時変数の変数を置き換える`b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   ローカルの共通部分式最適化では、コンパイラは共通部分式のコードの短いセクションを調べます。 グローバルの共通部分式最適化では、コンパイラは、すべての関数に共通部分式を検索します。

- 自動レジスタ割り当て

   この最適化により、レジスタにも、コンパイラは頻繁に使用されるストアの変数と部分式`register`キーワードは無視されます。

- ループの最適化

   この最適化では、ループの本体からインバリアント部分式を削除します。 最適なループには、ループの各実行により変更する値を持つ式のみが含まれています。 次の例では、式で`x + y`ループの本体が変更されていません。

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   最適化後`x + y`ループが実行されるたびにではなく 1 回計算されます。

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   コンパイラ偽物ではなく、エイリアスで設定するときに、ループの最適化がはるかに効果的[_ _restrict](../../cpp/extension-restrict.md)、 [noalias](../../cpp/noalias.md)、または[制限](../../cpp/restrict.md)します。

   > [!NOTE]
   > 有効にまたはを使用して、関数ごとにグローバルな最適化を無効にすることができます、`optimize`プラグマと組み合わせて、`g`オプション。

関連情報については、次を参照してください。 [/Oi (組み込み関数の生成)](oi-generate-intrinsic-functions.md)と[/Ox (有効にする最もの速度の最適化)](ox-full-optimization.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. コンパイラ オプションを入力して、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
