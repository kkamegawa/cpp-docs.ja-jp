---
title: /POGOSAFEMODE (スレッド セーフ モードで実行 PGO)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: bbb328bf67d7823305a43f1d61252747cf5ea29e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319721"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/POGOSAFEMODE (スレッド セーフ モードで実行 PGO)

**Visual Studio 2015 以降では、/POGOSAFEMODE オプションは非推奨**します。 使用して、 [/GENPROFILE: 正確な](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)と **/GENPROFILE:NOEXACT**オプションの代わりにします。 **/POGOSAFEMODE**リンカー オプションは、スレッド セーフ モードを使用して、トレーニングの実行プロファイル ガイド付き最適化の (PGO) の中にプロファイル データのキャプチャをインストルメント化されたビルドが作成されたことを指定します。

## <a name="syntax"></a>構文

> **/POGOSAFEMODE**

## <a name="remarks"></a>Remarks

最適化のガイド付きプロファイル (PGO) が、プロファイリング フェーズ中に 2 つのモードを持つ:*高速モード*と*セーフ モード*します。 高速モードでプロファイリングを行う、データ カウンター数を増やしますインクリメント命令が使用されます。 インクリメント命令は高速ですが、スレッド セーフではありません。 セーフ モードでプロファイリングを行う、データ カウンター数を増やしますインタロックされたインクリメント命令が使用されます。 この命令は、同じ機能を低速ですが、増分命令とスレッド セーフです。

**/POGOSAFEMODE**オプションは、セーフ モードを使用してインストルメント化されたビルドを設定します。 このオプションはのみに際に使用される、非推奨[/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) PGO インストルメンテーション リンカーのフェーズ中に指定されました。

既定では、PGO プロファイリングは高速モードで動作します。 **/POGOSAFEMODE**がセーフ モードを使用するかどうかにのみ必要です。

セーフ モードでの PGO プロファイリングを実行する、いずれかを使用する必要があります **/GENPROFILE: 正確な**(推奨)、環境変数を使用または[PogoSafeMode](../environment-variables-for-profile-guided-optimizations.md)かリンカー スイッチ **/POGOSAFEMODE**、システムによって異なります。 x64 コンピューターでプロファイリングを実行する場合は、リンカー スイッチを使用する必要があります。 X86 でプロファイリングを実行するかどうか、コンピューター リンカー スイッチを使用するか、PGO インストルメンテーションのプロセスを開始する前に、任意の値を環境変数を定義することがあります。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **最適化**プロパティ ページ。

1. **リンク時コード生成**プロパティ選択**ガイド付き最適化のプロファイル - インストルメント (//ltcg:pginstrument)** します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. 入力、 **/POGOSAFEMODE**にオプション、**追加オプション**ボックス。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/GENPROFILE と/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)<br/>
[ガイド付き最適化のプロファイルの環境変数](../environment-variables-for-profile-guided-optimizations.md)<br/>
