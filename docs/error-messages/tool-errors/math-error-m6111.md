---
title: 数値演算エラー M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393409"
---
# <a name="math-error-m6111"></a>数値演算エラー M6111

スタックのアンダー フロー

浮動小数点演算では、8087/287/387 コプロセッサまたはエミュレーター スタック アンダー フローが発生しました。

呼び出しによってこのエラーが原因となった多くの場合、`long double`値を返さない関数。 たとえば、次このエラーを生成コンパイルと実行。

```
long double ld() {};
main ()
{
  ld();
}
```

終了コード 139 でプログラムを終了します。