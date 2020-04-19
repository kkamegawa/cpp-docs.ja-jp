---
title: /HIGHENTROPYVA (64 ビット ASLR のサポート)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 5ecbbf8bbd8e74f80f2f5b2d7df0d2ef544112fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291601"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (64 ビット ASLR のサポート)

実行可能ファイル イメージが高いエントロピの 64 ビット ASLR (Address Space Layout Randomization) をサポートするかどうかを指定します。

## <a name="syntax"></a>構文

> **/HIGHENTROPYVA** **[:NO]**

## <a name="remarks"></a>Remarks

**/HIGHENTROPYVA**のヘッダーを変更、*実行可能イメージ*、.dll ファイルまたは .exe ファイル、ASLR が全体の 64 ビット アドレス空間を使用できるかどうかを示す。 このオプションを実行可能ファイルおよび依存するモジュールのすべてに設定すると、64 ビット ASLR をサポートするオペレーティング システムは、読み込み時に 64 ビットの仮想アドレス空間でランダム化されたアドレスを使用して、実行可能イメージのセグメントのベース アドレスをリベースできます。 この大きいアドレス空間により、攻撃者は特定のメモリ領域の位置を推測することが困難となります。

既定では、 **/HIGHENTROPYVA** 64 ビット実行可能イメージが有効になっています。 このオプションが必要です[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)も 64 ビット イメージに対して既定で有効になっています。 **/HIGHENTROPYVA**適用可能でない、32 ビット実行可能イメージに、リンカーが、オプションを無視します。 このオプションを明示的に無効にするには、 **/HIGHENTROPYVA:NO**します。

**/HIGHENTROPYVA** 、読み込み時に影響する[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)も有効にする必要があります。 **/DYNAMICBASE**が既定では、有効になり、ASLR の Windows Vista 以降のオペレーティング システムで有効にするために必要な。 Windows の以前のバージョンでは、このフラグを無視します。

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. **追加オプション**、入力`/HIGHENTROPYVA`または`/HIGHENTROPYVA:NO`します。

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Windows ISV Software Security Defenses](https://msdn.microsoft.com/library/bb430720.aspx)
