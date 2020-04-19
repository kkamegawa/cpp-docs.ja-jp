---
title: /GENPROFILE、/FASTGENPROFILE (プロファイル インストルメント ビルドの生成)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: cf6327b175344f1e2914792eb47a4838e544ea24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292212"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (プロファイル インストルメント ビルドの生成)

ガイド付き最適化のプロファイル (PGO) をサポートするために、リンカーによる .pgd ファイルの生成を指定します。 **/GENPROFILE**と **/FASTGENPROFILE**異なる既定のパラメーターを使用します。 使用 **/GENPROFILE**速度とメモリ使用量をプロファイリング中に有効桁数を優先するようにします。 使用 **/FASTGENPROFILE**精度より小さいメモリ使用量と速度を優先するようにします。

## <a name="syntax"></a>構文

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]<br/>
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]

### <a name="arguments"></a>引数

指定する、次の引数のいずれかを **/GENPROFILE**または **/FASTGENPROFILE**します。 ここで表示されている引数をパイプで区切られて (**|**) 文字は相互に排他的です。 コンマを使用して (**、**) オプションを区切る文字。

**COUNTER32** &AMP;#124; **COUNTER64 です**<br/>
使用して、 **COUNTER32** 32 ビットのプローブのカウンターの使用を指定して**COUNTER64**を 64 ビットのプローブのカウンターを指定します。 指定すると **/GENPROFILE**、既定値は**COUNTER64**します。 指定すると **/FASTGENPROFILE**、既定値は**COUNTER32**します。

**正確な** &AMP;#124; **、NOEXACT です**<br/>
使用**EXACT**プローブのスレッド セーフであるインター ロックされたインクリメントを指定します。 **Noexact は、** プローブの保護されていないインクリメント操作を指定します。 既定値は**noexact は、** します。

**MEMMAX**=*値*、 **MEMMIN**=*値*<br/>
使用**MEMMAX**と**MEMMIN**をメモリ内のトレーニング データの最大値と最小の予約サイズを指定します。 値は、予約するメモリ量 (バイト単位) です。 既定では、これらの値は内部ヒューリスティックによって決定されます。

**PATH**  &#124; **NOPATH** <br/>
使用**パス**関数への各一意のパスの PGO カウンターの個別セットを指定します。 使用**場合は、NOPATH**関数の各カウンターの 1 つだけのセットを指定します。 指定すると **/GENPROFILE**、既定値は**パス**します。 指定すると **/FASTGENPROFILE**、既定値は**場合は、NOPATH**します。

**TRACKEH**  &#124; **NOTRACKEH** <br/>
トレーニング中に例外がスローされた場合に、追加のカウンターを使用して正確なカウントを保持するかどうかを指定します。 使用**TRACKEH**正確な数の追加のカウンターを指定します。 使用して、 **NOTRACKEH**例外を使用しないコードの 1 つのカウンターを指定するまたは処理しない例外が発生しない、トレーニング シナリオでします。  指定すると **/GENPROFILE**、既定値は**TRACKEH**します。 指定すると **/FASTGENPROFILE**、既定値は**NOTRACKEH**します。

**PGD**=*ファイル名*<br/>
.pgd ファイルの基本ファイル名を指定します。 既定では、リンカーは、基本の実行可能イメージのファイル名に .pgd 拡張子を付けて使用します。

## <a name="remarks"></a>Remarks

**/GENPROFILE**と **/FASTGENPROFILE**オプション付き最適化のプロファイル (PGO) のアプリケーション トレーニングをサポートするために必要なプロファイル インストルメンテーション ファイルを生成するリンカーに指示します。 これらのオプションは、Visual Studio 2015 の新機能です。 非推奨とされるこれらのオプションを優先 **/LTCG:PGINSTRUMENT**、 **/PGD**と **/POGOSAFEMODE**オプションと**PogoSafeMode**、 **VCPROFILE_ALLOC_SCALE**と**VCPROFILE_PATH**環境変数。 アプリケーションのトレーニングによって生成されたプロファイル情報が、ビルド中に入力として使用され、対象のプログラム全体の最適化が実行されます。 アプリのトレーニング中とビルド中にパフォーマンスのためのさまざまなプロファイル機能を制御する追加のオプションを設定することができます。 既定のオプションを指定して **/GENPROFILE**特に大規模で複雑なマルチ スレッド アプリケーション用の最も正確な結果を提供します。 **/FASTGENPROFILE**オプションは、メモリ フット プリントの削減と精度と引き換えに、トレーニング中にパフォーマンスを向上させるさまざまな既定値を使用します。

使用してビルドした後に、インストルメント化されたアプリを実行するときに、プロファイル情報がキャプチャ **/GENPROFILE**の **/FASTGENPROFILE**します。 指定すると、この情報がキャプチャされた、 [/USEPROFILE](useprofile.md)リンカー オプション、プロファイリングを実行する手順し、最適化されたビルド手順をガイドするために使用します。 アプリをトレーニングする方法の詳細と、収集したデータの詳細については、次を参照してください。[ガイド付き最適化の](../profile-guided-optimizations.md)します。

指定する必要がありますも **/LTCG**を指定すると **/GENPROFILE**または **/FASTGENPROFILE**します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. 入力、 **/GENPROFILE**または **/FASTGENPROFILE**オプションと引数、**追加オプション**ボックス。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[/LTCG (リンク時のコード生成)](ltcg-link-time-code-generation.md)<br/>
