---
title: /USEPROFILE (LTCG を使用して PGO のデータ)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 7bc0033ae5ef512cbd2e2063c5cb9bd9b061c180
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317134"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (スレッド セーフ モードで実行 PGO)

このリンカー オプションと共に[/LTCG (リンク時コード生成](ltcg-link-time-code-generation.md)トレーニング データの最適化のガイド付きプロファイル (PGO) を使用してビルドをリンカーに指示します。

## <a name="syntax"></a>構文

> **/USEPROFILE**[**:**{**AGGRESSIVE**|**PGD=**_filename_}]

### <a name="arguments"></a>引数

**アグレッシブです**<br/>
この省略可能な引数では、最適化されたコードの生成中にアグレッシブな速度の最適化を使用することを指定します。

**PGD**=*ファイル名*<br/>
.pgd ファイルの基本ファイル名を指定します。 既定では、リンカーは、.pgd 拡張子を持つベースの実行可能ファイル名を使用します。

## <a name="remarks"></a>Remarks

**/USEPROFILE**リンカー オプションと共に使用 **/LTCG**を生成または PGO トレーニング データに基づく最適化されたビルドを更新します。 非推奨とされるのと同じ **/LTCG:PGUPDATE**と **/LTCG:PGOPTIMIZE**オプション。

省略可能な**アグレッシブな**引数には、速度を最適化しようとするサイズに関連するヒューリスティックが無効にします。 これにより、最適化を大幅に、実行可能ファイルのサイズを増やすし、結果として得られる速度を上げることがありますいない可能性があります。 プロファイルし、使用と不使用の結果を比較する必要があります**アグレッシブな**します。 この引数を明示的に指定する必要があります。既定で無効です。

**PGD** 、オプションと同様、使用するトレーニング データの .pgd ファイルの名前を指定する引数[/GENPROFILE または/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)します。 非推奨とされるのと同じ **/PGD**スイッチします。 既定では、ない場合、または*filename*が指定されている .pgd ファイルを実行可能ファイルに使用されているために、同じ基本名を持ちます。

**/USEPROFILE**リンカー オプションは Visual Studio 2015 の新機能です。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **最適化**プロパティ ページ。

1. **リンク時コード生成**プロパティ選択**使用リンク時コード生成 (/LTCG)** します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. 入力、 **/USEPROFILE**オプション、および省略可能な引数に、**追加オプション**ボックス。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/GENPROFILE と/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)<br/>
[ガイド付き最適化のプロファイルの環境変数](../environment-variables-for-profile-guided-optimizations.md)<br/>
