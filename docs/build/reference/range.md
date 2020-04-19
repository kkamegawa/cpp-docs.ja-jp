---
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: c631057e47e1a52a58d2b1304133dfdfc008ae14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319708"
---
# <a name="range"></a>/RANGE

Dumpbin/RAWDATA または/DISASM など、他の dumpbin オプションと共に使用する場合の出力を変更します。

## <a name="syntax"></a>構文

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>パラメーター

*vaMin*<br/>
Dumpbin 操作を開始する仮想アドレス。

*vaMax*<br/>
(省略可能)Dumpbin 操作が終了するたい仮想アドレス。 指定しない場合、dumpbin は、ファイルの末尾に移動します。

## <a name="remarks"></a>Remarks

イメージの仮想アドレスを表示するイメージ (RVA + ベース) のマップ ファイルを使用して、 **/DISASM**または **/HEADERS** dumpbin、または Visual Studio デバッガーで逆アセンブル ウィンドウのオプション。

## <a name="example"></a>例

この例で**範囲/** の表示を変更するために使用、 **/disasm**オプション。 この例では、開始値は 10 進数として表現し、終了値は 16 進数として指定します。

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
