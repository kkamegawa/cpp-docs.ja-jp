---
title: /GT (スレッド ローカル ストレージを使用したファイバー保護のサポート)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 417ac00a446f773a424553e42478a4f0cf58efc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291809"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (スレッド ローカル ストレージを使用したファイバー保護のサポート)

静的スレッド ローカル ストレージを使用して割り当てられたデータを使用して割り当てられたデータに対して、ファイバー保護をサポートしている`__declspec(thread)`します。

## <a name="syntax"></a>構文

```
/GT
```

## <a name="remarks"></a>Remarks

宣言されたデータ`__declspec(thread)`スレッド ローカル ストレージ (TLS) の配列を使用して参照されます。 TLS の配列は、各スレッドに対して、システムが保持しているアドレスの配列です。 この配列内の各アドレスは、スレッド ローカル ストレージのデータの場所を示します。

ファイバーは、軽量オブジェクトをスタックとレジスタのコンテキストで構成され、さまざまなスレッドでスケジュールできます。 ファイバーは、任意のスレッドで実行できます。 ファイバーはスワップ アウトが後に別のスレッドで再起動ため、TLS の配列のアドレスする必要がありますいないキャッシュまたは最適化される共通部分式として関数呼び出しの間で (を参照してください、 [/Og (グローバルの最適化)](og-global-optimizations.md)オプション詳細情報)。 **/GT**このような最適化を防止します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**最適化**プロパティ ページ。

1. 変更、**ファイバー保護の最適化を有効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
