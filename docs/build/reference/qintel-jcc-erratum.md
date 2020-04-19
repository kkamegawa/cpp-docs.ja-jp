---
title: /QIntel-jcc-erratum
description: Microsoft C/C++コンパイラ (MSVC)/QIntel-jcc-erratum オプションについて説明します。
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520919"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

**/QIntel-jcc-erratum**オプションは、Visual Studio 2019 バージョン16.5 以降で使用できます。

::: moniker-end

::: moniker range=">=vs-2019"

特定の Intel プロセッサにおける Intel ジャンプ条件付きコード (JCC) erratum マイクロコード更新によって引き起こされるパフォーマンスへの影響を軽減するための命令をコンパイラが生成するように指定します。

## <a name="syntax"></a>構文

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Remarks

**/QIntel-jcc-erratum**の下では、コンパイラは、32バイトの境界で交差または終了するジャンプ命令とマクロのヒューズを検出します。 これらの命令は境界に合わせて配置されます。 この変更により、特定の Intel プロセッサで JCC erratum が妨げられるマイクロコード更新のパフォーマンスへの影響が軽減されます。 Erratum の詳細については、Intel の web サイトの「[ジャンプ条件付きコード erratum の対応策](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf)」を参照してください。

**/QIntel-jcc-erratum**オプションは、Visual Studio 2019 バージョン16.5 以降で使用できます。 このオプションは、x86 および x64 を対象とするコンパイラでのみ使用できます。 このオプションは、ARM プロセッサを対象とするコンパイラでは使用できません。

**/QIntel-jcc-erratum**オプションは、既定ではオフになっており、最適化されたビルドでのみ機能します。 このオプションを使用すると、コードサイズを増やすことができます。

**/QIntel-jcc-erratum**は[/clr](clr-common-language-runtime-compilation.md)と互換性がありません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **[構成プロパティ]** > [ **CC++ /** >**コード生成**] プロパティページを選択します。

1. **[Intel JCC Erratum 軽減策を有効にする]** プロパティの値を選択します。 **[OK]** を選択して変更を適用します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[/Q オプション (低レベルの操作)](q-options-low-level-operations.md)\
[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)

::: moniker-end
