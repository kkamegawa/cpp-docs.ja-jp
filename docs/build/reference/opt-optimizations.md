---
title: /OPT (最適化)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: 1a6fa8b9c923ff697831c29b8004ce360baf7d77
ms.sourcegitcommit: ae2f71fe0d64f1a90ef722759fe93c82abc064ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53587890"
---
# <a name="opt-optimizations"></a>/OPT (最適化)

LINK がビルド時に実行する最適化を制御します。

## <a name="syntax"></a>構文

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_イテレーション_] |**NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>引数

**REF** &AMP;#124; **NOREF**

**/OPT:REF**関数と; 参照されないデータを排除 **/OPT:NOREF**関数および参照されないデータが保持されます。

未参照のパッケージ化された関数と呼ばれる、データ リンクの削除/OPT:REF を有効にすると、 *Comdat*します。 この最適化は、中間 COMDAT 除去として知られています。 **/OPT:REF**もオプションではインクリメンタル リンクを無効になります。

インライン関数とクラス宣言内で定義されているメンバー関数は comdat 形式では常にです。 すべてのオブジェクト ファイルに関数を使用してコンパイルされる場合 Comdat を行う、 [/Gy](../../build/reference/gy-enable-function-level-linking.md)オプション。 配置する**const** comdat 形式でデータをする必要がありますを宣言することを使用して`__declspec(selectany)`します。 データの削除または折りたたみを指定する方法については、次を参照してください。 [selectany](../../cpp/selectany.md)します。

既定では、 **/OPT:REF**がリンカーによって有効になっていない限り **/OPT:NOREF**または[/debug](../../build/reference/debug-generate-debug-info.md)を指定します。 この既定のオーバーライドをプログラムで参照されない Comdat の保持は、次のように指定します。 **/OPT:NOREF**します。 使用することができます、 [/include](../../build/reference/include-force-symbol-references.md)特定のシンボルの削除のオーバーライド オプションを指定します。

場合[/debug](../../build/reference/debug-generate-debug-info.md)指定するの既定の **/opt**は**NOREF**、し、すべての関数は、イメージに保存されます。 この既定のオーバーライドをデバッグ ビルドの最適化は、次のように指定します。 **/OPT:REF**します。 これは、実行可能ファイルのサイズを小さくことができ、デバッグの場合でも有効な最適化を構築することができます。 指定することをお勧めします。 **/OPT:NOICF**構築デバッグ機能と同じに維持します。 これにより、スタック トレースを読み取って、圧縮された関数にブレークポイントを設定しやすくなります。

**ICF**\[**=**_イテレーション_] &#124; **NOICF**

使用**ICF**\[**=**_イテレーション_] と同一の COMDAT の圧縮を実行します。 リンカー出力から余分な COMDAT シンボルを削除できます。 省略可能な*イテレーション*パラメーターをシンボル重複の走査回数を指定します。 既定のイテレーションの数には 1 です。 イテレーションの回数を増やすと、前回のイテレーションで圧縮されなかった重複が検出されることがあります。

既定では、 **/OPT:ICF**がリンカーによって有効になっていない限り **/OPT:NOICF**または[/debug](../../build/reference/debug-generate-debug-info.md)を指定します。 この既定をオーバーライドし、プログラムで折りたたまれているから Comdat を防止するのには、指定 **/OPT:NOICF**します。

デバッグ ビルドである必要があります明示的に指定する **/OPT:ICF** COMDAT の圧縮を有効にします。 ただし、ため **/OPT:ICF**同一のデータや関数をマージすることができます、スタック トレースに表示される関数名を変更することができます。 またなります。 あり得ないのは、特定の関数にブレークポイントを設定するか、デバッガーでのいくつかのデータを確認し、予期しない関数にかかるときに、コードをシングル ステップ実行します。 コードの動作は同じですが、デバッガーのプレゼンテーションを非常に混乱を招くことができます。 そのため、しないで使用する **/OPT:ICF**デバッグでより小さなコードの利点がこうした欠点を上回らない限りが構築されます。

> [!NOTE]
> **/OPT:ICF**異なる関数または読み取り専用データ メンバーに割り当てられるのと同じアドレスが発生することができます (つまり、 **const**を使用してコンパイルするときに変数 **/Gy**)、関数または読み取り専用データ メンバーの一意のアドレスに依存するプログラムを壊すことできます。 詳細については、「[/Gy (関数レベルのリンクの有効化)](../../build/reference/gy-enable-function-level-linking.md)」を参照してください。

**LBR** &AMP;#124; **NOLBR**

**/OPT:LBR**と **/OPT:NOLBR**オプション ARM バイナリのみに適用されます。 特定の ARM プロセッサの分岐命令の範囲が限られているため、リンカーは、範囲外のアドレスへのジャンプを検出すると、分岐命令の終点アドレスを、実際の終点を対象とする分岐命令を含むコード "アイランド" のアドレスに置き換えます。 使用することができます **/OPT:LBR**長い分岐命令の検出とコード全体のサイズを最小限に抑える中間コード アイランドの配置を最適化します。 **/OPT:NOLBR**リンカー最適化を行わず、検出されると、長い分岐命令のコード アイランドを生成するように指示します。

既定で、 **/OPT:LBR**インクリメンタル リンクが有効でない場合、オプションを設定します。 非インクリメンタル リンクですがない時間の長い分岐命令の最適化をする場合、指定 **/OPT:NOLBR**します。 **/OPT:LBR**オプションは、インクリメンタル リンクを無効になります。

## <a name="remarks"></a>Remarks

コマンドラインで使用する場合、リンカー既定 **/OPT:REF、ICF、LBR**します。 場合 **/debug**を指定すると、既定値は **/OPT:NOREF、NOICF、NOLBR**します。

**/Opt**最適化は一般にイメージのサイズを小さくと、プログラムの実行速度を向上します。 これらの機能強化は、製品版ビルドの既定で有効になっている理由で大規模なプログラムは、大幅なでができます。

リンカー最適化事前に余分な時間がかかり、最適化されたコードを処理し、pdb ファイルに書き込むには、少ないデバッグ情報があるときにさらに多くの時間が節約して、リンカーが少ないの再配置を修正するし小さいの最終的なイメージを作成するタイミングをも保存します。 最適化を有効にすると、そのようリンク時間が高速で全体的に見て、分析で小規模の追加コストがするによって相殺リンカーを大幅に節約小さいバイナリが置かれた時間とします。

**/Opt**引数が同時に指定する、コンマで区切られました。 たとえばの代わりに **/OPT:REF/OPT:NOICF**を指定できます **/OPT:REF、NOICF**します。

使用することができます、 [/verbose](../../build/reference/verbose-print-progress-messages.md)によって削除される関数を表示するリンカー オプション **/OPT:REF**および関数によって折りたたむが **/OPT:ICF**します。

**/Opt**引数は多くの場合を使用して作成されたプロジェクトの設定、**新しいプロジェクト**ダイアログは、Visual Studio IDE で、通常、デバッグに別の値を持って構成とリリース構成します。 プロジェクトでこれらのリンカー オプションの値が設定されていない場合は、プロジェクトの既定値は、コマンドラインで、リンカーによって使用される既定値と異なる場合がありますを取得可能性があります。

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境で OPT:ICF リンカー オプションまたは OPT:REF リンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **最適化**プロパティ ページ。

1. 次のいずれかのプロパティを変更します。

   - **COMDAT の圧縮を有効にします。**

   - **参照**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境で OPT:LBR リンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. オプションを入力して**追加オプション**:

   `/opt:lbr` または `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> プロパティおよび <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> プロパティを参照してください。

## <a name="see-also"></a>関連項目

- [リンカー オプションの設定](../../build/reference/setting-linker-options.md)
- [リンカー オプション](../../build/reference/linker-options.md)
