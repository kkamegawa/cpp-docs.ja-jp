---
title: /Ob (関数のインライン展開)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915480"
---
# <a name="ob-inline-function-expansion"></a>/Ob (関数のインライン展開)

関数のインライン展開を制御します。 既定では、最適化すると、すべての関数に対するコンパイラの裁量によって展開が行われます。これは、多くの場合、*自動インライン展開*と呼ばれます。

## <a name="syntax"></a>構文

::: moniker range=">=vs-2019"

> **/Ob**{**0**|**1**|**2**|**3**}

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob**{**0**|**1**|**2**}

::: moniker-end

## <a name="arguments"></a>引数

**0**\
[/Od](od-disable-debug.md)の既定値。 インライン展開を無効にします。

**1**\
[inline](../../cpp/inline-functions-cpp.md)、 [__inline](../../cpp/inline-functions-cpp.md)、または[__forceinline](../../cpp/inline-functions-cpp.md)とマークされた関数、またはC++クラス宣言で定義されているメンバー関数の展開のみを許可します。

**2**\
[/O1](o1-o2-minimize-size-maximize-speed.md)と[/O2](o1-o2-minimize-size-maximize-speed.md)の既定値。 明示的にインライン禁止とマークされていない関数をコンパイラで展開できるようにします。

::: moniker range=">=vs-2019"

**3**\
このオプションは、 **/Ob2** よりも積極的なインライン展開を指定しますが、同じ制限があります。 **/Ob3** オプションは、Visual Studio 2019 以降で使用できます。

::: moniker-end

## <a name="remarks"></a>Remarks

インライン展開に関するオプションとキーワードは、インライン展開の対象となる候補をコンパイラに示すだけです。 関数がインラインで展開される保証はありません。 インライン展開を無効にすることはできますが、 `__forceinline`キーワードを使用している場合でも、特定の関数のインライン化をコンパイラに強制することはできません。

インライン展開の候補として関数を除外するには、 [__declspec (noinline)](../../cpp/noinline.md)、または [#pragma auto_inline (off)](../../preprocessor/auto-inline.md) ディレクティブと [#pragma auto_inline (on)](../../preprocessor/auto-inline.md) ディレクティブでマークされた領域を使用できます。 コンパイラにインライン展開ヒントを提供する別の方法については、「 [#pragma intrinsic](../../preprocessor/intrinsic.md) ディレクティブ」を参照してください。

> [!NOTE]
> プロファイリングテストの実行から収集された情報は、 **/Ob**、 **/Os**、または **/Ot** を指定したために適用される最適化よりも優先されます。 詳細については、[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md) を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **構成プロパティ**  >  **C/C++**  >  **最適化** プロパティページを選択します。

1. **インライン関数の展開**プロパティを変更します。

::: moniker range=">=vs-2019"

**/Ob3**オプションは、 **[インライン関数の展開]** プロパティでは使用できません。 **/Ob3** を設定する方法は以下のとおりです。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **構成プロパティ** > **C/C++** > **コマンドライン** プロパティページを選択します。

1. **追加のオプション**に「 **/Ob3** 」と入力します。

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>

## <a name="see-also"></a>関連項目

[/O オプション (コードの最適化)](o-options-optimize-code.md)\
[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
