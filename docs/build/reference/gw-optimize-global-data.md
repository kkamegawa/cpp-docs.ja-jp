---
title: /Gw (グローバル データの最適化)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 8afdb21defbbc8309b27749ab18a40f9555139e5
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450135"
---
# <a name="gw-optimize-global-data"></a>/Gw (グローバル データの最適化)

グローバル データを最適化のために COMDAT セクションにパッケージ化します。

## <a name="syntax"></a>構文

```
/Gw[-]
```

## <a name="remarks"></a>Remarks

**/Gw**オプションは、個々 の COMDAT セクションで、パッケージのグローバル データ コンパイラ。 既定では、 **/Gw**がオフと明示的に有効にする必要があります。 これを明示的に無効にするを使用して **/Gw-** します。 ときに両方 **/Gw**と[/GL](gl-whole-program-optimization.md)が有効にすると、リンカーを使用してプログラム全体の最適化またはマージする参照されないグローバル データを除外するために複数のオブジェクト ファイルの COMDAT セクションを比較するには同一読み取り専用のグローバル データ。 その結果、生成されるバイナリ実行可能ファイルのサイズが大幅に小さくなることがあります。

コンパイルしてリンクを別々 に使用できます、 [/OPT:REF](opt-optimizations.md)でコンパイルされたオブジェクト ファイルで参照されないグローバル データの実行可能ファイルから除外するリンカー オプション、 **/Gw**オプション。

使用することも、 [/OPT:ICF](opt-optimizations.md)と[/LTCG](ltcg-link-time-code-generation.md)で複数のオブジェクト ファイルと同じ読み取り専用グローバル データがコンパイルされた実行可能ファイルにマージするリンカー オプション、 **/Gw**オプション。

詳細については、次を参照してください。 [Introducing/Gw コンパイラ スイッチ](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/)上、C++チームのブログ。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Gw**選び、 **OK**します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
