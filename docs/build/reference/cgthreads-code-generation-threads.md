---
title: /cgthreads (コード生成スレッド)
ms.date: 11/04/2016
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: df353eb255c731478863ed6088cafa1cc38053fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294695"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (コード生成スレッド)

最適化とコード生成に使用するための cl.exe スレッドの数を設定します。

## <a name="syntax"></a>構文

```
/cgthreads[1-8]
```

## <a name="arguments"></a>引数

*number*<br/>
cl.exe が使用できるスレッドの最大数で、1 から 8 の範囲。

## <a name="remarks"></a>Remarks

**/Cgthreads**オプションは、cl.exe のスレッドの最大数を使用して並列での最適化およびコード コンパイルの生成のフェーズを指定します。 できませんの間にスペースに注意してください。 **/cgthreads**と`number`引数。 既定では、cl.exe は 4 つのスレッドを使用する場合と **/cgthreads4**指定されました。 より多くのプロセッサ コアが使用できる場合、より大きい `number` 値はビルド時間を改善できます。 このオプションと結合されている場合に特に役立ちます[/GL (Whole Program Optimization)](gl-whole-program-optimization.md)します。

ビルドでは複数のレベルの並列化を指定できます。 Msbuild.exe スイッチ **/maxcpucount**並列に実行できる MSBuild プロセスの数を指定します。 [/MP (複数のプロセスを使用したビルド)](mp-build-with-multiple-processes.md)コンパイラ フラグを同時にソース ファイルをコンパイルする cl.exe プロセスの数を指定します。 **/Cgthreads**オプションは、それぞれの cl.exe プロセスで使用されるスレッドの数を指定します。 プロセッサは、プロセッサ コアの数しかスレッドを同時に実行できないため、これらすべてのオプションに、より大きな値を同時に設定するのは効果的ではなく、逆効果になる場合もあります。 プロジェクトの並行ビルドする方法の詳細については、次を参照してください。[複数プロジェクトの並行ビルド](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ**、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/cgthreads**`N`ここで、`N`は 1 から 8 の値を選び**OK**。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
