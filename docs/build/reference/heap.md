---
title: /HEAP
ms.date: 11/04/2016
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: fcf557b467ba5bd04352ba2f2702659a1eb2948d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291991"
---
# <a name="heap"></a>/HEAP

ヒープのサイズをバイト単位で設定します。 このオプションは、実行可能ファイルにのみ適用されます。

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>Remarks

`reserve`引数は、仮想メモリの合計の初期ヒープ割り当てを指定します。 既定では、ヒープ サイズは、1 MB です。 [EDITBIN リファレンス](editbin-reference.md)指定した値は 4 バイトの倍数に丸めます。

省略可能な`commit`引数は、オペレーティング システムによって解釈されるは。 Windows オペレーティング システムで割り当てるには、物理メモリの初期量と、ヒープを展開する必要がありますを割り当てるための追加のメモリの量を指定します。 仮想メモリがコミットされると、ページング ファイル内にメモリ空間が予約されます。 高度な`commit`値は、アプリは、ヒープ領域を増やす必要がありますが、メモリの量とアプリのスタートアップ時間が増加しているときに多くの場合、メモリの少ない割り当てにシステムを使用します。 `commit`値に等しいまたはそれよりも小さくなければなりません、`reserve`値。

指定、`reserve`と`commit`10 進数または 16 進数または 8 進数の C 言語表記の値。 たとえば、1048576 10 進数、または 16 進数、0x100000 または 8 進数で 04000000 は、1 MB の値を指定できます。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)
