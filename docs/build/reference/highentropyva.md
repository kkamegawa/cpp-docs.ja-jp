---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270225"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

実行可能ファイル イメージが高いエントロピの 64 ビット ASLR (Address Space Layout Randomization) をサポートするかどうかを指定します。

## <a name="syntax"></a>構文

> **/HIGHENTROPYVA** **[:NO]**

## <a name="remarks"></a>Remarks

このオプションのヘッダーを変更する、*実行可能イメージ*、.dll ファイルまたは .exe ファイルを 64 ビット アドレスの ASLR がサポートされているかどうかを示します。 このオプションを実行可能ファイルおよび依存するモジュールのすべてに設定すると、64 ビット ASLR をサポートするオペレーティング システムは、読み込み時に 64 ビットの仮想アドレス空間でランダム化されたアドレスを使用して、実行可能イメージのセグメントのベース アドレスをリベースできます。 この大きいアドレス空間により、攻撃者は特定のメモリ領域の位置を推測することが困難となります。

既定では、リンカーができるように **/HIGHENTROPYVA** 64 ビット実行可能ファイルのイメージ。 このオプションが必要です[/LARGEADDRESSAWARE](largeaddressaware.md)も 64 ビット イメージに対して既定で有効になっています。 **/HIGHENTROPYVA**は、32 ビット実行可能イメージに適用可能なオプションが無視されます。 このオプションを明示的に無効にするには、 **/HIGHENTROPYVA:NO**します。 このオプションに影響を与える、 [/DYNAMICBASE](dynamicbase.md)オプションも設定する必要があります。

## <a name="see-also"></a>関連項目

- [EDITBIN オプション](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Windows ISV Software Security Defenses](https://msdn.microsoft.com/library/bb430720.aspx)
