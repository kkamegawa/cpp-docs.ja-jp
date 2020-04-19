---
title: /Oi (組み込み関数の生成)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: f3afedade6f99129c21069e5117daa4ceb616cc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320345"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (組み込み関数の生成)

いくつかの関数呼び出し、アプリケーションに役立つ固有またはそれ以外の場合に特殊な形式の関数を置き換えますが速くなります。

## <a name="syntax"></a>構文

```
/Oi[-]
```

## <a name="remarks"></a>Remarks

組み込み関数を使用するプログラムは、高速関数の呼び出しのオーバーヘッドはありませんが、追加のコードを作成したので大きい可能性があります、ためにです。

参照してください[組み込み](../../preprocessor/intrinsic.md)詳細については関数が組み込みのフォームがあります。

**/Oi**に一部の関数呼び出しを置き換える組み込み; コンパイラに要求のみ、コンパイラが関数を呼び出し (を関数呼び出しを組み込みで置き換える) のパフォーマンスが向上が得られる場合。

**x86 固有**

浮動小数点の組み込み関数がなく入力値に対して、特別なチェックを実行しそのため、入力の範囲の制限で作業、さまざまな例外処理と同じ名前のライブラリ ルーチンより境界条件。 本物の組み込み形式を使用して、IEEE 例外処理の損失とのことを意味`_matherr`と`errno`機能です。 後者の ansi 規格適合性が失われることを意味します。 ただし、組み込み形式は、浮動小数点を多用するプログラムをかなり高速化でき、準拠の問題が実用的価値のほとんどは、多くのプログラムにします。

使用することができます、 [Za](za-ze-disable-language-extensions.md)コンパイラ オプションを true 組み込み浮動小数点オプションの生成をオーバーライドします。 浮動小数点関数はライブラリ ルーチンとして生成されます。これらのライブラリ ルーチンでは、引数はプログラム スタックにプッシュされずに、数値演算コプロセッサに直接渡されます。

**END x86 固有**

使用することも[組み込み](../../preprocessor/intrinsic.md)の組み込み関数を作成するまたは[関数 (C++)](../../preprocessor/function-c-cpp.md)を関数呼び出しを明示的に適用します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**最適化**プロパティ ページ。

1. 変更、**組み込み関数の有効化**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>

## <a name="see-also"></a>関連項目

[/O オプション (コードの最適化)](o-options-optimize-code.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[コンパイラの組み込み](../../intrinsics/compiler-intrinsics.md)
