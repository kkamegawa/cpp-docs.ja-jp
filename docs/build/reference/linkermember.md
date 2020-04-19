---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: a0456fd9ed1729b4a6cfa200a54ba211a64e94ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216586"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Remarks

このオプションは、ライブラリで定義されたパブリック シンボルを表示します。 そのオフセットと共に、オブジェクトの順序でシンボルを表示する 1 引数を指定します。 オフセットとオブジェクトのインデックス番号を表示する 2 つの引数を指定し、各オブジェクトのインデックスと共に、アルファベット順にシンボルを一覧表示します。 両方の出力を取得するには、数値の引数なし/LINKERMEMBER を指定します。

のみ、 [/HEADERS](headers.md) DUMPBIN オプションがで生成されたファイルで使用できる、 [/GL](gl-whole-program-optimization.md)コンパイラ オプション。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
